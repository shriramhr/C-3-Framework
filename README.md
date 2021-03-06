# **C**rowd **C**ounting **C**ode Framework (C^3-Framework) 

An open-source PyTorch code for crowd counting

---

This repo is under development. We will spare my spare time to develop it. 

If you have any question/suggestion/bug, please you submit the issue instead of email or other ways. 


## Goal

The purpose of this code is an efficient, flexible framework for supervised crowd counting. At the same time, we provide the performances of some basic networks and classic algorithms on the mainstream datasets.


## Features
- **Convenient development kit**. It is a convenient dev kit on the six maintream datasets.
- **Solid baselines**. It provides some baselines of some classic pre-trained models, such as AlexNet, VGG, ResNet and so on. Base on it, you can easily compare your proposed models' effects with them.
- **Powerful log**. It does not only record the loss, visulization in Tensorboard, but also save the current code package (including parameters settings). The saved code package can be directly ran to reproduce the experiments at any time. You won't be bothered by forgetting the confused parameters.


## Performance
Due to linmited spare time and the number of GPUs, I do not plan to conduct some experiments (named as "TBD"). If you are intested in the project, you are welcome to submit your own experimental parameters and results.

|          Method          |                GCC(rd,cc,cl)              | UCF-QNRF  |   SHT A   |  SHT B  |
|--------------------------|-------------------------------------------|-----------|-----------|---------|
| MCNN (RGB Image)         |102.2/238.3,     140.3/285.7,   176.1/373.9|243.5/364.7|110.6/171.1|23.9/42.7|
| AlexNet (conv5)          | 46.3/110.9,      83.7/180.3,   101.2/233.6|    TBD    |    TBD    |   TBD   |
| VGG-16 (conv4_3)         |  36.6/88.9,      57.6/133.9,    91.4/222.0|119.3/207.7|71.4/115.7 |10.3/16.5|
| VGG-16 (conv4_3)+decoder |  37.2/91.2,      56.9/138.3,    88.9/220.9|115.2/189.6|71.5/117.6 |10.5/17.4|
| ResNet-50 (layer3)       |  32.4/76.1,  **54.5/129.7**,**78.3/201.6**|    TBD    |    TBD    |7.7/12.6 |
| ResNet-101 (layer3)      |  31.9/81.4,      56.8/139.5,    86.9/214.2|    TBD    |    TBD    |   TBD   |
| CSRNet                   |  32.6/74.3,      54.6/135.2,    87.3/217.2|    TBD    |69.3/111.9 |10.6/16.6|
| SANet                    |  42.4/85.4,      79.3/179.9,   110.0/246.0|    TBD    |    TBD    |12.1/19.2|
| CMTL                     |                       -                   |    TBD    |    TBD    |    -    |
| SFCN (todo)              |                       -                   |           |           |         |
| ResSFCN-101 (SFCN+)      |  **26.8/66.1**,  56.5/139.0,    83.5/211.5|     -     |           |         |


|          Method          | WE |UCF50|
|--------------------------|----|-----|
| MCNN (RGB Image)         |TBD | TBD |
| AlexNet (conv5)          |TBD | TBD |
| VGG-16 (conv4_3)         |TBD | TBD |
| VGG-16 (conv4_3)+decoder |TBD | TBD |
| ResNet-50 (layer3)       |TBD | TBD |
| ResNet-101 (layer3)      |TBD | TBD |
| CSRNet                   |TBD | TBD |
| SANet                    |TBD | TBD |
| CMTL                     |TBD | TBD |
| SFCN                     |    |     |
| ResSFCN-101 (SFCN+)      |    |     |


### data processing code
- [x] GCC
- [x] UCF-QNRF
- [x] ShanghaiTech Part_A
- [x] ShanghaiTech Part_B
- [x] WorldExpo'10
- [x] UCF_CC_50


## Getting Started

### Preparation
- Prerequisites
  - Python 2.7
  - Pytorch 1.0 (some networks only support 0.4): http://pytorch.org .
  - other libs in ```requirements.txt```, run ```pip install -r requirements.txt```.


- Installation
  - Clone this repo:
    ```
    git clone https://github.com/gjy3035/C-3-Framework.git
    ```

- Data Preparation
  - In ```./datasets/XXX/readme.md```, download our processed dataset or run the ```prepare_XXX.m/.py``` to generate the desity maps. If you want to directly download all processeed data (including Shanghai Tech, UCF-QNRF, UCF_CC_50 and WorldExpo'10), please visit the [**link**](https://mailnwpueducn-my.sharepoint.com/:f:/g/personal/gjy3035_mail_nwpu_edu_cn/EkxvOVJBVuxPsu75YfYhv9UBKRFNP7WgLdxXFMSeHGhXjQ?e=IdyAzA).
  - Place the processed data to ```../ProcessedData```.

- Pretrained Model
  - Some Counting Networks (such as VGG, CSRNet and so on) adopt the pre-trained models on ImageNet. You can download them from [TorchVision](https://github.com/pytorch/vision/tree/master/torchvision/models)
  - Place the processed data to ```../PyTorch_Pretrained```.

- Folder Tree

    ```
    +-- C-3-Framework
    |   +-- datasets
    |   +-- misc
    |   +-- ......
    +-- ProcessedData
    |   +-- shanghaitech_part_A
    |   +-- ......
    +-- PyTorch_Pretrained
    |   +-- resnet50-19c8e357.pth
    |   +-- ......
    ```
    

### Training

- set the parameters in ```config.py``` and ```./datasets/XXX/setting.py```.
- run ```python train.py```.
- run ```tensorboard --logdir=exp --port=6006```.

### Testing

We only provide an examplar to test the model on the test set. Yopu may need to modify it to test your models.

### Citation
If you find this project useful for your research, please cite:
```
@inproceedings{wang2019learning,
  title={Learning from Synthetic Data for Crowd Counting in the Wild},
  author={Wang, Qi and Gao, Junyu and Lin, Wei and Yuan, Yuan},
  booktitle={Proceedings of IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
  year={2019}
}
```
```
@misc{gao2019c3framework,
author = {Gao, Junyu and Gao, Chenyu and Zeng, Xin and Qin, Zequn and Wen, Jun},
title = {C^3-Framework: An open-source PyTorch code for crowd counting},
year = {2019},
howpublished = {\url{https://github.com/gjy3035/C-3-Framework}}
}
```
