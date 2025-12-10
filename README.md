# Detecting Suspicious Activity in the NFT Ecosystem using Temporal Graph Analysis
This is the code for **[Detecting Suspicious Activity in the NFT Ecosystem using Temporal Graph Analysis](https://github.com/slitiWassim/Detecting-Suspicious-Activity-in-the-NFT-Ecosystem)** .

### [Project](https://slitiwassim.github.io/Detecting-Suspicious-Activity-in-the-NFT-Ecosystem/) | [Dataset]() | [Paper]()
 

## Framework Overview

<a href="static/images/framework_TKG.png" target="_blank">
    <image style="border: 2px solid rgb(201, 196, 196);" src="static/images/framework_TKG.png" width="100%">
</a>



## Setup
The code can be run under any environment with Python 3.12 and above.
(It may run with lower versions, but we have not tested it).

Install the required packages:

    pip install -r requirements.txt
  
Clone this repo:

    git clone https://github.com/slitiWassim/Detecting-Suspicious-Activity-in-the-NFT-Ecosystem.git
    cd Detecting-Suspicious-Activity-in-the-NFT-Ecosystem/

##  Data Collection and Preparation





<a href="static/images/data_collection_preparation.png" target="_blank">
    <image style="border: 2px solid rgb(201, 196, 196);" src="static/images/data_collection_preparation.png" width="100%">
</a>



A dataset is a directory with the following structure:
  ```bash
  $ tree data
  ped2/avenue
  ├── training
  │   └── mapping
  │       ├── ${video_1}$
  │       │   ├── 000.jpg
  │       │   ├── 001.jpg
  │       │   └── ...
  │       ├── ${video_2}$
  │       │   ├── 00.jpg
  │       │   └── ...
  │       └── ...
  └── testing
  
  ```

### Data description
| Descriptions | Statistics                                                                                  |
|--|---------------------------------------------------------------------------------------|
|Start date(dd-mm-yyyy,UTC) | 23-06-2017 21:05 |
|End date (dd-mm-yyyy, UTC)| 22-12-2023 19:06 |
|Number of NFT collections | 1,746,379 |
|Number of NFT tokens |41,292,572 |
|Number of account addresses| 7,062,831 |
|Number of transactions |77,735,708 |
|Chains | 10 |



## Temporal Cycles Detection

<a href="static/images/temporal_cycles.png" target="_blank">
    <image style="border: 2px solid rgb(201, 196, 196);" src="static/images/temporal_cycles.png" width="100%">
</a>


## Training
To train `Drone-Guard` on a dataset, run:
```bash
 python  train.py --cfg <config-file> --pseudo True
```  
 For example, to train `Drone-Guard` on Ped2:

```bash
python train.py \
    --cfg config/ped2.yaml \
    --pseudo True # To Train model with both normal and pseudo anomalies data
```


## Evaluation
Please first download the pre-trained model

| Dataset | Pretrained Model                                                                                  |
|--|---------------------------------------------------------------------------------------|
| UCSD Ped2 | [![Google drive](https://badgen.net/static/Link/Ped2/blue?icon=chrome)](https://drive.google.com/file/d/1M2zmfCxYB-f7e9zxoDzVeYxA7bcF8ock/view?usp=drive_link) |
| CUHK Avenue | [![Google drive](https://badgen.net/badge/Link/Avenue/blue?icon=chrome)](https://drive.google.com/file/d/1FE_ndmAgGbK7PWL0GbaQMYp6WplXeqWY/view?usp=drive_link) |
| ShanghaiTech | [![Google drive](https://badgen.net/badge/Link/ShanghaiTech/blue?icon=chrome)](https://drive.google.com/file/d/1bxOlFPju_LONHjJQlUo28dIpY8ZSucto/view?usp=drive_link) |
| Drone-Anomaly | [![Google drive](https://badgen.net/badge/Link/Drone-Anomaly/blue?icon=chrome)](https://drive.google.com/drive/folders/1MyzMWROIyj7iAHPFZmg1RD7QmW0CHzTU?usp=drive_link)    |

To evaluate a pretrained `Drone-Guard` on a dataset, run:

```bash
 python test.py \
    --cfg <path/to/config/file> \
    --pretrained </path/to/pre-trained/model> 
```      
 
 For example, to evaluate `Drone-Guard` on Ped2:

```bash
python test.py \
    --cfg config/ped2.yaml \
    --model-file  pre-trained/best_model_ped2.pth
```
<!-- 
## Training from scratch
To train `HSTforU` on a dataset, run:
```bash
python -m torch.distributed.launch \
    --nproc_per_node <num-of-gpus-to-use> \
    --master_port 12345  main.py \ 
    --cfg <path/to/config/file> \
    [--batch-size <batch-size-per-gpu> --tag <job-tag>]
```

For example, to train `HSTforU` on Ped2:

```bash
python -m torch.distributed.launch --nproc_per_node 4 --master_port 12345 train.py --cfg configs/scripts/ped2/ped2_pvt2_hst.yaml 
``` 
-->
## Configuration
 * We use [YAML](https://yaml.org/) for configuration.
 * We provide a couple preset configurations.
 * Please refer to `config.py` for documentation on what each configuration does.

## Citing
If you find our work useful, please consider citing:
```BibTeX
Paper submitted 

```

## Contact
For any question, please file an [issue](https://github.com/slitiWassim/Drone-Guard/issues) or contact:

    Wassim Sliti : wassim.sliti@upm.es

## Acknowledgement

This work was carried out within the STRAST Research Group at the Information Processing and Telecommunications Center (IPTC), Universidad Politécnica de Madrid, as part of the [ CEDAR ](https://cedar-heu-project.eu/)   project, funded by the Horizon Europe Programme (Grant Agreement No. 101135577). 