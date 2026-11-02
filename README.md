# Explainable and Adversarially Robust 1D-CNN Framework for Encrypted Network Traffic Classification

A comparative study of machine learning and deep learning approaches for encrypted network traffic classification, focusing on VPN detection, model explainability, and adversarial robustness.

## Overview

Encrypted network traffic limits traditional payload inspection techniques. However, statistical flow characteristics such as packet timing, inter-arrival times, and flow rates remain observable and can be used for traffic classification.

This research investigates whether deep learning models provide better performance, interpretability, and robustness than traditional machine learning approaches for encrypted VPN traffic classification.

Three approaches are evaluated:

1. Random Forest (RF)
2. Standard 1D Convolutional Neural Network (1D-CNN)
3. Improved 1D-CNN with Explainable AI and Adversarial Training

## Research Objectives

- Classify encrypted network traffic into VPN and Non-VPN categories.
- Compare traditional machine learning with deep learning architectures.
- Improve CNN architecture efficiency and reduce model parameters.
- Interpret model predictions using SHAP and LIME.
- Evaluate adversarial robustness using FGSM and PGD attacks.
- Analyze the impact of adversarial training on model performance.

## Dataset

**Dataset:** ISCX VPN-nonVPN Dataset

| Attribute | Details |
|---|---|
| Total flows | 18,758 |
| VPN flows | 9,793 |
| Non-VPN flows | 8,965 |
| Original statistical features | 23 |
| Selected features | 15 |
| Classification | Binary |

### Data Preprocessing

- Stratified 80:10:10 train-validation-test split.
- StandardScaler for feature normalization.
- Mutual Information for feature selection.
- Selection of 15 relevant features from 23 original features.
- Training-only fitting of the scaler and feature selection process.

## Methodology

### 1. Random Forest

A traditional machine learning baseline using:
- 200 decision trees
- Maximum depth of 20
- Balanced class weights

### 2. Standard 1D-CNN

A deep learning architecture consisting of:
- Two convolutional layers
- Batch normalization
- Max pooling
- Flatten layer
- Dense layer with dropout
- Sigmoid output layer

### 3. Improved 1D-CNN

An optimized architecture incorporating:
- Same-padded convolutional layers
- L2 regularization
- Batch normalization
- Global max pooling
- Two dense layers
- Increased dropout

The improved architecture reduces model complexity while maintaining comparable classification performance.

### 4. Explainable AI

Two explainability techniques are used:

- **SHAP:** Identifies feature contributions to model predictions.
- **LIME:** Explains individual predictions through local surrogate models.

### 5. Adversarial Robustness

The improved CNN is evaluated using:

- Fast Gradient Sign Method (FGSM)
- Projected Gradient Descent (PGD)
- FGSM-based adversarial training
- Random-noise control experiments
- Transfer attacks against the Random Forest

## Experimental Results

### Model Performance

| Metric | Random Forest | Standard CNN | Improved CNN |
|---|---:|---:|---:|
| Accuracy | 91.79% | 71.48% | 72.55% |
| Macro Precision | 0.9185 | 0.7143 | 0.7348 |
| Macro Recall | 0.9171 | 0.7145 | 0.7294 |
| Macro F1-score | 0.9176 | 0.7144 | 0.7246 |
| ROC-AUC | 0.9765 | 0.8025 | 0.8159 |
| Parameters | N/A | 58,625 | 12,993 |

### Key Findings

- Random Forest achieved the highest test accuracy of 91.79%.
- The improved CNN reduced the number of parameters by approximately 78% compared with the standard CNN.
- SHAP revealed differences in feature importance between Random Forest and CNN models.
- Adversarial training improved FGSM resistance but did not provide complete protection against PGD attacks.
- Model accuracy alone is insufficient to establish robustness.

## Technology Stack

- **Programming Language:** Python
- **Deep Learning:** TensorFlow
- **Machine Learning:** Scikit-learn
- **Explainable AI:** SHAP, LIME
- **Data Processing:** NumPy, Pandas
- **Visualization:** Matplotlib, Seaborn
- **Environment:** Google Colab / Jupyter Notebook

## Repository Structure

```text
Research-Paper/
│
├── WORKINGMODEL.ipynb
├── README.md
└── requirements.txt
```

## How to Run

1. Clone this repository:

```bash
git clone https://github.com/shahharshita78-cpu/Research-Paper.git
```

2. Navigate to the project directory:

```bash
cd Research-Paper
```

3. Install the required dependencies:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn tensorflow shap lime scipy
```

4. Open the Jupyter Notebook:

```bash
jupyter notebook WORKINGMODEL.ipynb
```

5. Make the ISCX VPN-nonVPN dataset available and configure its path as required by the notebook.

6. Execute the notebook cells to run the experiments.

## Limitations and Future Work

- Evaluation is based on one dataset and one flow timeout.
- The classification task is limited to VPN and Non-VPN traffic.
- Adversarial perturbations are not constrained to physically realizable network flows.
- Session-level data splitting and cross-network generalization require further investigation.

Future work includes:
- PGD-based adversarial training.
- Log-scaled feature transformations.
- Realistic, flow-constrained adversarial attacks.
- Session-level data splitting.
- Multi-class application traffic classification.

## Authors

- Harshita Shah
- Aditi Singh
- Vinikesh Hiranandani
- Shreyansh Mohanty

Department of Computer Engineering & Technology  
Dr. Vishwanath Karad MIT World Peace University, Pune, India.

---

**Research Focus:** Encrypted Network Traffic Classification | Explainable AI | Adversarial Machine Learning | Deep Learning Security
