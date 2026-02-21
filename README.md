# Gene Expression Cancer Prediction

Machine learning classification of **acute myeloid leukemia (AML)** vs. **acute lymphoblastic leukemia (ALL)** subtypes using high-dimensional RNA gene expression data, achieving an **F1 score of 0.95**.

## Overview

Accurate classification of leukemia subtypes is critical for treatment planning — AML and ALL require fundamentally different therapeutic approaches. This project applies machine learning to gene expression profiles (7,000+ features) to distinguish between these two cancer subtypes, demonstrating that computational methods can reliably automate what traditionally requires specialized pathological analysis.

## Key Results

| Metric | Score |
|--------|-------|
| **F1 Score** | **0.95** |
| **Accuracy** | 95.8% |
| **Precision** | 0.94 |
| **Recall** | 0.96 |

## Approach

### The Challenge
Gene expression data is inherently high-dimensional — each sample contains expression levels for 7,000+ genes, but the dataset contains far fewer samples. This creates a classic *p >> n* problem where overfitting is a major risk and feature selection is critical.

### Pipeline

1. **Data Preprocessing**
   - Log2 transformation of raw expression values
   - Standardization (zero mean, unit variance)
   - Handling of missing values via median imputation

2. **Feature Selection**
   - Univariate statistical testing (t-tests with Bonferroni correction)
   - Recursive Feature Elimination (RFE)
   - Variance-based filtering to remove low-information genes
   - Final feature set reduced from 7,000+ to most discriminative genes

3. **Model Training & Evaluation**
   - Logistic Regression (L1/L2 regularization)
   - Support Vector Machines (RBF kernel)
   - Random Forest Classifier
   - Stratified k-fold cross-validation (k=5)
   - Evaluated on held-out test set

4. **Interpretability**
   - Feature importance ranking to identify top discriminative genes
   - Biological validation of top-ranked genes against known leukemia biomarkers

## Dataset

The dataset contains gene expression measurements from leukemia patients:
- **Features:** 7,129 gene expression levels per sample
- **Classes:** AML (Acute Myeloid Leukemia) vs. ALL (Acute Lymphoblastic Leukemia)
- **Source:** Microarray gene expression profiling

## Tech Stack

- Python 3.x
- scikit-learn
- pandas, NumPy
- matplotlib, seaborn
- Jupyter Notebook

## Key Takeaways

- **Dimensionality reduction is essential** — models trained on the full 7,000+ feature space overfit significantly; feature selection improved generalization by ~12%
- **Regularized linear models compete with ensembles** — L1-regularized logistic regression performed comparably to random forests, suggesting that the decision boundary is approximately linear in the selected feature space
- **Biologically meaningful features emerge** — top-ranked genes by feature importance overlap with known AML/ALL biomarkers, providing confidence that the model captures real biological signal

## Author

**Samir Kerkar**  
University of California, Irvine — B.S. Mathematics  
Samir2000VIP@gmail.com
