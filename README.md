# [Vision-Language Transformer and Query Generation for Referring Segmentation](https://arxiv.org/abs/2108.05565)

Please consider citing our paper in your publications if the project helps your research.
```
@inproceedings{vision-language-transformer,
  title={Vision-Language Transformer and Query Generation for Referring Segmentation},
  author={Ding, Henghui and Liu, Chang and Wang, Suchen and Jiang, Xudong},
  booktitle={Proceedings of the IEEE International Conference on Computer Vision},
  year={2021}
}
```

## Introduction

Vision-Language Transformer (VLT) is a framework for referring segmentation task. Our method produces multiple query vector for one input language expression, and use each of them to “query” the input image, generating a set of responses. Then the network selectively aggregates these responses, in which queries that provide better comprehensions are spotlighted.

<p align="center">
<img src="fig0.png" width="500px">
</p>

## Installation

1. Environment:

   - Python 3.6
   - tensorflow 1.15
   - Other dependencies in `requirements.txt`
   - SpaCy model for embedding: 
      
      ```python -m spacy download en_vectors_web_lg```
   - **Note from Yash** — Install `pycocotools==2.0.0` with pip after installing requirements.txt

2. Dataset preparation (**Note from Yash -- not needed since we use custom data**)

   - Put the folder of COCO training set ("`train2014`") under `data/images/`.

   - Download the RefCOCO dataset from [here](https://github.com/lichengunc/refer) and extract them to `data/`. Then run the script for data preparation under `data/`:
   
      ```
      cd data
      python data_process_v2.py --data_root . --output_dir data_v2 --dataset [refcoco/refcoco+/refcocog] --split [unc/umd/google] --generate_mask
      ```

## Evaluating

1. Download pretrained models & config files from [here](https://entuedu-my.sharepoint.com/:f:/g/personal/liuc0058_e_ntu_edu_sg/EpE88e5DW1NEl6p7sKlMvrcBhBLeMTuHbtNKDiJCvhQBtQ?e=6thFDa). 

2. **Note from Yash --** Make sure you have downloaded `log/refcocop_example/models/best_map.h5` checkpoint from above.

3. See `add_ref.md` for how to run. 