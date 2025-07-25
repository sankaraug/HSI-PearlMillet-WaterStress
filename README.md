# UAV-Based Hyperspectral Imaging Dataset of Pearl Millet Water Stress

This repository contains the dataset description, preprocessing workflow, benchmark model implementations, and performance results as described in the IEEE paper:

**"UAV-Borne Hyperspectral Imaging Dataset of Pearl Millet Canopy Water Stress"**  
[IEEE](https://ieeexplore.ieee.org/document/9881337) *(published in ICA 2024)*



## Dataset Overview

- **Crop**: Pearl Millet
- **Sensor**: Resonon Pika-L HSI camera (282 bands, 400–1000 nm)
- **Platform**: DJI Matrice-600 Pro UAV
- **Water Treatments**: Well-Watered (WW), Water-Stressed (WS)
- **Stress Levels**: WS1 (12 days after irrigation stopped), WS2 (18 days)
- **Genotypes**: 350 varieties × (4 WW + 5 WS) replications
- **Samples**: 25×25×282 HS image patches

| Dataset | Total Samples | Train Samples | Test Samples |
|---------|----------------|----------------|----------------|
| WW vs WS1 | 10,399 | 4662 | 5737 |
| WW vs WS2 | 5718  | 2667 | 3051 |


## Dataset Access (via TiHAN Server)

Due to data size and controlled access requirements, the dataset is hosted on the **TiHAN server**.

📝 **[Request Dataset Access](https://tihan.server.org/request-access)** 

> Access will be granted upon filling a form explaining your research purpose.



## Dataset Creation Workflow

Steps followed as per the paper:

1. **Radiometric Calibration** – Convert raw DN to radiance and reflectance.
2. **Geometric Rectification** – Remove motion distortion, geo-align plots.
3. **Image Quality Check** – NIQE used for filtering.
4. **Denoising** – Using FastHyDe for spectral consistency.
5. **Patch Extraction** – NDVI > 0.7, TCARI > 1300 based segmentation.



## Benchmark Models

The following models are implemented for classification:

- `SVM` (Spectral classifier)
- `3D-CNN`
- `2D+1D CNN`
- `3D-CAE`
- `ViT` (Vision Transformer)
- `SpectralFormer`

You’ll find implementation scripts under [`code/classification/`](./code/classification/).



## Performance Metrics

| Model | WW-WS1 OA (%) | WW-WS2 OA (%) |
|-------|----------------|----------------|
| SVM | 77.87 | 79.82 |
| 3D-CAE | 81.31 | 92.19 |
| 2D+1D CNN | 73.01 | 88.59 |
| 3D-CNN | 82.07 | 88.52 |
| ViT | 81.26 | 89.92 |
| SpectralFormer | 81.51 | **93.88** |



## Folder Structure

```bash
HSI-PearlMillet-WaterStress/
├── dataset/                # Dataset metadata, access instructions
│   └── README.md
├── code/                  # All model and preprocessing code
│   ├── preprocessing/
│   ├── classification/
│   └── utils/
├── models/                # Trained model weights 
├── results/               # Graphs, OA scores, confusion matrices
├── LICENSE
├── CITATION.bib
└── README.md
```



## Citation

```bibtex
@inproceedings{sankararao2025hsi,
  author    = {Sankararao, Adduru U. G. and Kiran, Sai and Rajalakshmi, P. and Choudhary, Sunita},
  title     = {UAV-Borne Hyperspectral Imaging Dataset of Pearl Millet Canopy Water Stress},
  booktitle = {International Conference on Advances in Computing},
  year      = {2025},
  doi       = {10.1007/978-3-031-74440-2_19}
}
```



## Contributors

- Dr. Adduru U.G. Sankararao – IIT Hyderabad
- Mr. Sai Kiran – IIT Hyderabad
- Prof. P. Rajalakshmi – Research Advisor
- Dr. Sunita Choudhary – Scientist, ICRISAT 


## Notes

- Pretrained models may be shared later depending on approval.
- Suggestions/Issues welcome via GitHub Issues.



© 2025 IIT Hyderabad & ICRISAT – All Rights Reserved.
