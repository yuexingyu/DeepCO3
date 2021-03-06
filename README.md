# [CVPR19] DeepCO<sup>3</sup>: Deep Instance Co-segmentation by Co-peak Search and Co-saliency (Oral paper)
### Authors: [Kuang-Jui Hsu](https://www.citi.sinica.edu.tw/pages/kjhsu/), [Yen-Yu Lin](https://www.citi.sinica.edu.tw/pages/yylin/index_en.html), [Yung-Yu Chuang](https://www.csie.ntu.edu.tw/~cyy/)

+ PDF: [High-Resolution](http://cvlab.citi.sinica.edu.tw/images/paper/cvpr-hsu19.pdf), [Low-Resolution](http://cvlab.citi.sinica.edu.tw/images/paper/cvpr-hsu19-lowres.pdf)
+ Supplementary material: [High-Resolution](https://drive.google.com/file/d/1zNB1oydDUMQGLbZie1rJgvHTPjmDnYTC/view?usp=sharing), [Low-Resolution](https://drive.google.com/file/d/1aYR88gVmZHedZUK43M49MqZVWQ4z3A8F/view?usp=sharing)

## Abstract
In this paper, we address a new task called instance cosegmentation. Given a set of images jointly covering object instances of a specific category, instance co-segmentation aims to identify all of these instances and segment each of them, i.e. generating one mask for each instance. This task is important since instance-level segmentation is preferable for humans and many vision applications. It is also challenging because no pixel-wise annotated training data are available and the number of instances in each image is unknown. We solve this task by dividing it into two sub-tasks, co-peak search and instance mask segmentation. In the former sub-task, we develop a CNN-based network to detect the co-peaks as well as co-saliency maps for a pair of images. A co-peak has two endpoints, one in each image, that are local maxima in the response maps and similar to each other. Thereby, the two endpoints are potentially covered by a pair of instances of the same category. In the latter subtask, we design a ranking function that takes the detected co-peaks and co-saliency maps as inputs and can select the object proposals to produce the final results. Our method for instance co-segmentation and its variant for object colocalization are evaluated on four datasets, and achieve favorable performance against the state-of-the-art methods.

## Examples 
Two examples of instance co-segmentation on categories bird and sheep, respectively. An instance here refers to an object appearing in an image. In each example, the top row gives the input images while the bottom row shows the instances segmented by our method. The instance-specific coloring indicates that our method produces a segmentation mask for each instance.

<p align="center">
<img src="https://github.com/KuangJuiHsu/DeepCO3/blob/master/Image/CVPR19_Example.PNG" width="800"/>
</p>

## Overview of our method
The proposed method contains two stages, co-peak search within the blue-shaded background and instance mask segmentation within the red-shaded background. For searching co-peaks in a pair of images, our model extracts image features, estimates their co-saliency maps, and performs feature correlation for co-peak localization. The model is optimized by three losses, including the co-peak loss, the affinity loss, and the saliency loss. For instance mask segmentation, we design a ranking function taking the detected co-peaks, the co-saliency maps, and the object proposals as inputs, and select the top-ranked proposal for each detected instance.

<p align="center">
<img src="https://github.com/KuangJuiHsu/DeepCO3/blob/master/Image/CVPR19_Overview.PNG" height="400"/>
</p>

## Results
+ Instance co-segmentation

The performance of instance co-segmentation on the four collected datasets is shown. The numbers in red and green show the best and the second best results, respectively. The column “trained” indicates whether additional training data are used.
<p align="center">
<img src="https://github.com/KuangJuiHsu/DeepCO3/blob/master/Image/CVPR19_InstCoSeg.PNG"/>
</p>

+ Object co-localization

The performance of object co-localization on the four datasets is shown. The numbers in red and green indicate the best and the second best results, respectively. The column “trained” indicates whether additional training data are used.
<p align="center">
<img src="https://github.com/KuangJuiHsu/DeepCO3/blob/master/Image/CVPR19_ObjCoLoc.PNG"/>
</p>

<p>Please cite our paper if this code is useful for your research.</p>
<pre><code>
@inproceedings{HsuCVPR19,
  author = {Kuang-Jui Hsu and Yen-Yu Lin and Yung-Yu Chuang},
  booktitle = {IEEE Computer Society Conference on Computer Vision and Pattern Recognition (CVPR)},
  title = {DeepCO$^3$: Deep Instance Co-segmentation by Co-peak Search and Co-saliency Detection},
  year = {2019}
}
</code></pre>

---
# Codes for DeepCO<sup>3</sup>

- Contact: [Kuang-Jui Hsu](https://www.citi.sinica.edu.tw/pages/kjhsu/)
- Last update: 2019/04/09
- Platform: Ubuntu 14.04, [MatConvnet 1.0-beta24](http://www.vlfeat.org/matconvnet/) (Don't support any installation problem of MatConvnet.)


## Demo for all stages: "RunDeepInstCoseg.m"
- Including all files in "Lib" (Downloading MatConvnet is not necessary)
- May be slightly different from the ones in paper because of the randdom seeds

## Datasets (about 34 GB):
- Including four collected datasets
- Containing the images, ground-truth masks, salinecy maps and object proposals
- [GoogleDrive](https://drive.google.com/file/d/1IDyC8NXQdOZEaji6GKQZbh9uZ5B2r_79/view?usp=sharing)

## Results reported in the papers (about 4 GB):
- Only including the results of DeepCO<sup>3</sup> 
- [GoogleDrive](https://drive.google.com/file/d/1sMr11hbmc6w3GZAOKy5pbEZxyHBJtb8z/view?usp=sharing)

## Download Codes from GoogleDrive :
- [GoogleDrive](https://drive.google.com/file/d/1NnEVkrrrYyi5oNRKuIlQ6dkdupC5kHbB/view?usp=sharing)

---
# Errata:
- Thank [Howard Yu-Chun Lo](https://github.com/howardyclo/papernotes/issues/51) for pointint the typo in Eq. (4). The corrected one is listed in the following: 
<p align="center">
<img src="https://github.com/KuangJuiHsu/DeepCO3/blob/master/Image/CVPR19_Errata_Eq4.PNG"/>
</p>
