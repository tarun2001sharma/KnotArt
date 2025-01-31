# KnotArt

This repository contains the PyTorch code for 
"[Search Me Knot, Render Me Knot: Embedding Search and Differentiable Rendering of Knots in 3D](https://arxiv.org/abs/2307.08652)".

## Contents

1. [Introduction](#introduction)
2. [Installation](#installation)
3. [Usage](#usage)
4. [Dataset](#dataset)
5. [Results](#results)

## Introduction

We introduce the problem of knot-based inverse perceptual art. Given multiple target images and their corresponding viewing configurations, the objective is to find a 3D knot-based tubular structure whose appearance resembles the target images when viewed from the specified viewing configurations. To solve this problem, we first design a differentiable rendering algorithm for rendering tubular knots embedded in 3D for arbitrary perspective camera configurations. Utilizing this differentiable rendering algorithm, we search over the space of knot configurations to find the ideal knot embedding. We represent the knot embeddings via homeomorphisms of the desired template knot, where the homeomorphisms are parametrized by the weights of an invertible neural network. Our approach is fully differentiable, making it possible to find the ideal 3D tubular structure for the desired perceptual art using gradient-based optimization. We propose several loss functions that impose additional physical constraints, enforcing that the tube is free of self-intersection, lies within a predefined region in space, satisfies the physical bending limits of the tube material and the material cost is within a specified budget. We demonstrate through results that our knot representation is highly expressive and gives impressive results even for challenging target images in both single view as well as multiple view constraints. Through extensive ablation study we show that each of the proposed loss function is effective in ensuring physical realizability. We construct a real-world 3D-printed object to demonstrate the practical utility of our approach. To the best of our knowledge, we are the first to propose a fully differentiable optimization framework for knot-based inverse perceptual art.

<table width="100%">
  <tr>
    <td><img src="https://github.com/aalok1993/KnotArt/blob/main/assets/knotart_teaser_gallery.png"/></td>
    <td><img src="https://github.com/aalok1993/KnotArt/blob/main/assets/DancerA.png"/></td>
  </tr>
  <tr>
    <td><img src="https://github.com/aalok1993/KnotArt/blob/main/assets/knotart_teaser_front.png"/></td>
    <td><img src="https://github.com/aalok1993/KnotArt/blob/main/assets/DancerB.png"/></td>
  </tr>
  <tr>
    <th><center>Alphabetical Images</center></th>
    <th><center>Dancing Person Image Sequence</center></th>
  </tr>
</table>

## Installation

```
conda env create -f knotart.yml
```

OR

```
conda create -n knotart python=3.9
conda activate knotart
conda install pytorch==1.12.1 torchvision==0.13.1 torchaudio==0.12.1 cudatoolkit=11.3 -c pytorch
pip install opencv-python==4.6.0.66 numpy matplotlib Pillow
```


## Usage

For running with the ellipse renderer
```
python main.py
```

For running with the capsule renderer
```
python main.py --renderer_type capsule --num_samp 100
```
## Dataset

We introduce a novel dataset comprising multiple target images and their corresponding viewing configurations, designed specifically for evaluating knot-based inverse perceptual art. The dataset, along with loading scripts, is available under the `dataset` directory.

## Results

<table width="100%">
  <tr>
    <td><img src="https://github.com/aalok1993/KnotArt/blob/main/assets/ResultsWithConstraint.png"/></td>
    <td><img src="https://github.com/aalok1993/KnotArt/blob/main/assets/ResultsWithoutConstraints.png"/></td>
  </tr>
  <tr>
    <th><center>Results with constraints</center></th>
    <th><center>Results without constraints</center></th>
  </tr>
</table>




<table width="100%">
  <th colspan=2><center>Optimization Evolution</center></th>
  <tr>
    <td colspan=2><img src="https://github.com/aalok1993/KnotArt/blob/main/assets/Optimization_Evolution.gif"/></td>
  </tr>
  <tr>
    <th><center>Spatiotemporal Knots Front View</center></th>
    <th><center>Spatiotemporal Knots Side View</center></th>
  </tr>
  <tr>
    <td><img src="https://github.com/aalok1993/KnotArt/blob/main/assets/Spatiotemporal_Knots_Front_View.gif"/></td>
    <td><img src="https://github.com/aalok1993/KnotArt/blob/main/assets/Spatiotemporal_Knots_Side_View.gif"/></td>
  </tr>
</table>


## Citing

If you find KnotArt useful in your research, please consider citing:

```bibtex
@article{gangopadhyay2023searchmeknot,
  title={Search Me Knot, Render Me Knot: Embedding Search and Differentiable Rendering of Knots in 3D},
  author={Gangopadhyay, Aalok and Gupta, Paras and Sharma, Tarun and Singh, Prajwal and Raman, Shanmuganathan},
  journal={arXiv preprint arXiv:2307.08652},
  year={2023}
}
```




## Authors and Contributions

- Aalok Gangopadhyay - [GitHub Profile](https://github.com/aalok1993)
- Paras Gupta - [GitHub Profile](https://github.com/paras-gupt)
- Tarun Sharma - [GitHub Profile](https://github.com/tarun2001sharma)
- Prajwal Singh - [GitHub Profile](https://github.com/prajwalsingh)
- Shanmuganathan Raman

For detailed contributions, please refer to the paper.
