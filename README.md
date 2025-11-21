# StormWave: Multi-Scale Wavelet Disentanglement for Precipitation Nowcasting

By Baitian Liu, Haiping Zhang, and Xujian Fang*.

Department of Computer Science and Technology, Hangzhou Dianzi University



**The source code will be released upon publication.**



> *Corresponding author: Xujian Fang

> Last updated: Nov 21 / 2025



## Introduction

StormWave is a multi-scale wavelet disentanglement model for precipitation nowcasting,  we propose a `DetailNetwork + ApproximationNetwork + Refiner` architecture that separately learns large-scale patterns(A coefficient) and local details(D coefficients).

This repository contains the part of training and inference code for running StormWave to make predictions (6 --> 6) on SEVIR datasets.



## SEVIR Dataset

**S**torm **EV**ent **I**mage**R**y (SEVIR) dataset is a spatiotemporally aligned dataset containing over 10,000 weather events. We adopt NEXRAD Vertically Integrated Liquid (VIL) mosaics in SEVIR for benchmarking precipitation nowcasting, i.e., to predict the future VIL up to 6\*10 minutes given 6\*10 minutes context VIL. The resolution is thus `6×384×384→6×384×384`.

We thank AWS for providing online download service, for more details please refer to [AWS - Storm EVent ImageRy (SEVIR)](https://registry.opendata.aws/sevir/)



The dataloder returns a dict: 

```python
{
  "sequence": torch.Tensor,
  "target": torch.Tensor,
}
```

Each tensor's shape is `(Batch, 6, 128, 128)`.



## Code



### Enviroment

```bash
conda env create -f env.yaml
conda activate stormwave
```



### Resource

Pretrained weight: 



### Evaluation

Open `eval.py` file, and replace the weight file path to your path. Then run the command:

```bash
python eval.py 
```



### Training

In `train.py` file, we have provided the hyper-parameters that we use in experiments.

```python
python train.py
```



When you start training, these folders may offer you useful informations:

- `logs`  All the metrics during training have been recorded in this file, including hyper-parameters.
- `checkpoints` Mode weight file.



## Citation

```
@article{StromWave2025,
  author = {Baitian, Liu and Haiping, Zhang and Xujian, Fang},
  title = {StormWave: Multi-Scale Wavelet Disentanglement for Precipitation Nowcasting},
  journal = {Geophysical Research Letters},
  volume = {},
  number = {},
  pages = {},
  doi = {},
  url = {},
  year = {2025}
}

```



## Credit

Our implementation is heavily inspired by the following excellent works. We extend our thanks to the original authors.



Third-party libraries:

- [PyTorch](https://pytorch.org/)
- [PyTorch Lightning](https://www.pytorchlightning.ai/)
- [Muon](https://github.com/KellerJordan/Muon)



We refer to implementations of the following repositories and sincerely thank their contribution for the community.

- [pySTEPS](https://pysteps.github.io/) - BSD-3-Clause license
- [U-Net](https://github.com/himashi92/vanila-unet/blob/master/model/Unet.py)
- [ConvLSTM](https://github.com/Hzzone/Precipitation-Nowcasting/blob/master/nowcasting/models/convLSTM.py)
- [EarthFarseer](https://github.com/Alexander-wu/EarthFarseer)
- [SimVP](https://github.com/A4Bio/SimVP)
- [AlphaPre](https://github.com/linkenghong/AlphaPre)
- [FACL](https://github.com/argenycw/FACL) - MIT License