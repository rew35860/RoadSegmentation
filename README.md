# RoadSegmentation

[![Kaggle Rank](https://img.shields.io/badge/Kaggle-5th%20Place-gold.svg)](https://www.kaggle.com/competitions/ethz-cil-road-segmentation-2024)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📌 Project Overview
This repository contains the implementation for the **Road Segmentation** challenge, a part of the Computational Intelligence Lab (CIL) at **ETH Zürich**. The objective was to perform pixel-wise semantic segmentation on high-resolution aerial imagery to distinguish road networks from complex backgrounds.

### 🏆 Achievement
* **Final Rank:** 5th Place out of all participating teams.
* **Performance Metric:** Achieved an **F1-score of 0.93255**.

---

## 🛠 Methodology & Architecture
The solution utilizes a multi-stage approach combining state-of-the-art discriminative models with generative refinement.

### 1. Primary Segmentation: U-Net++
[cite_start]I employed a **U-Net++ (Nested U-Net)** architecture, which improves on the standard U-Net by using nested, dense skip pathways to reduce the semantic gap between encoder and decoder features[cite: 30, 31].
* **Backbone:** **EfficientNet-B7** (Pre-trained on ImageNet) was used as the encoder for its superior feature extraction capability.
* **Input Resolution:** 608x608 pixels.

### 2. Generative Refinement: GAN-based Post-processing
To ensure topological consistency (e.g., closing gaps in roads caused by tree cover), I implemented a refinement pipeline:
* **Pix2Pix:** A conditional GAN used to "translate" noisy raw masks into clean, sharpened segmentation maps.
* **CycleGAN:** Utilized to improve model robustness against domain shifts in satellite imagery.

---

## 📂 Dataset
* **Source:** 144 aerial images from Google Maps.
* **Ground Truth:** Each pixel is assigned a probabilistic label in [0,1], where 1 represents road and 0 represents background.

---
