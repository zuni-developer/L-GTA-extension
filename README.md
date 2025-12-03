# 📘 **L-GTA Extension: Adaptive Augmentation Controller (AAC)**

This repository provides a clean re-implementation of **L-GTA (Latent Generative Time-series Augmentation)** along with a newly designed extension called **AAC (Adaptive Augmentation Controller)**.
AAC introduces feature-aware latent-space policies that dynamically adjust augmentation strength and type for each time series, enabling richer and more realistic synthetic data across diverse domains.

---

## 📁 **Repository Structure**

```
├── L_GTA(BASE).ipynb               
├── LGTA_Adaptive_Augmentation_Controller.ipynb
├── datasets/
│   ├── tourism_groups_M__None_None.pickle
│   ├── M5_groups_W__None_500.pickle
│   └── police_groups_D__None_500.pickle
└── README.md
```

---

## 🚀 **Features**

### **1. Baseline L-GTA Implementation**

The baseline model includes:

* Conditional Variational Autoencoder (CVAE)
* GRU encoder–decoder architecture
* Latent-space perturbations:
  * Scaling
  * Shifting
  * Noise injection
  * Latent rotation
  * Combined perturbations
* Synthetic time-series generation
* Reconstruction quality evaluation
* Latent space visualization (PCA, scatter)

---

### **2. AAC (Adaptive Augmentation Controller)**

AAC enhances L-GTA by selecting augmentation strategies **based on statistical characteristics** of each series, making augmentation more realistic and domain-aligned.

#### **Extracted Features**

AAC computes several interpretable time-series features:

* Standard deviation
* Trend direction
* Linear slope
* Skewness
* Kurtosis
* Autocorrelation strength

#### **Feature-Driven Augmentation Policies**

AAC adaptively chooses:

* ✔ Scaling
* ✔ Shifting
* ✔ Noise injection
* ✔ Latent rotation
* ✔ Combined policies
* ✔ Intensity tuning per series

This makes AAC especially robust for:

* Highly non-stationary data
* Seasonal time series
* Smooth, low-variance series
* Series with shocks/outliers
* Real-world noisy datasets

---

## 📊 **Supported Datasets**

| Dataset            | Domain              | Size    | Purpose                      |
| ------------------ | ------------------- | ------- | ---------------------------- |
| **Tourism**        | Visitor forecasting | 304×204 | Baseline L-GTA demonstration |
| **M5 (Walmart)**   | Sales forecasting   | 500×261 | Large-scale evaluation       |
| **Police Dataset** | Crime patterns      | 500×T   | Non-stationary domain        |

---

## 🛠 **Installation**

Install dependencies:

```bash
pip install numpy scipy scikit-learn matplotlib tensorflow statsmodels pickle5
```

CPU works fine; GPU is optional.

---

## ▶ **How to Run the Notebooks**

### **1. Baseline L-GTA**

Run:

`L_GTA(BASE).ipynb`

This notebook:

* Loads datasets
* Builds the CVAE
* Performs latent perturbations
* Generates synthetic series
* Visualizes reconstructions and latent space

---

### **2. AAC — Adaptive Augmentation Controller**

Run:

`LGTA_Adaptive_Augmentation_Controller.ipynb`

This notebook:

* Loads datasets
* Trains new CVAE models
* Extracts statistical features
* Predicts augmentation policies
* Generates feature-aware augmented data
* Visualizes:

  * Original vs Augmented
  * ACF preservation
  * Distribution shift
  * Latent PCA
  * Multi-series overlays

---

## 📈 **Generated Outputs**

Both notebooks automatically produce:

* Reconstruction plots
* Synthetic vs real comparisons
* AAC vs basic augmentation
* Histograms of distribution shift
* Autocorrelation (ACF) plots
* Latent space PCA scatter
* Multi-series overlay plots
* Augmented datasets saved as `.npz`

---

## 🧪 **AAC Workflow Summary**

1. Load dataset
2. Normalize time series
3. Train CVAE
4. Encode into latent space
5. Extract statistical features
6. Select augmentation policy
7. Apply latent transformations
8. Decode into time-series
9. Visualize & compare outputs

---

## 📚 **Citation**

If you use this work, please cite the original L-GTA paper:

**Roque, L., Soares, C., Cerqueira, V. and Torgo, L., 2025. L-GTA: Latent Generative Modeling for Time Series Augmentation. arXiv preprint arXiv:2507.23615.**

---
