# News Recommendation System - MIND Dataset

**Author:** Vaishnavi Kamdi (G48986897)  
**Course:** CSCI6365 Advanced Machine Learning, George Washington University  
**Assignment:** Homework 2 - News Feed Recommendation

## Overview

This project implements and evaluates five recommendation approaches on the MIND (Microsoft News Dataset):
1. Most Popular Baseline
2. ALS Matrix Factorization
3. Item-based Collaborative Filtering
4. Content-Based Filtering
5. Hybrid Model (CF + Popularity)

## Project Structure

```
HW2/
├── README.md                           # This file
├── HW2_Report_with_table.tex          # Final report (LaTeX source)
├── notebooks/
│   ├── MIND_Dataset_Exploration.ipynb # Exploratory Data Analysis
│   └── MIND_Model_Implementation.ipynb # Model implementation & evaluation
├── data/
│   ├── MINDsmall_train.zip            # Training data (download from Kaggle)
│   └── MINDsmall_dev.zip              # Development/test data
├── processed_data/                     # Intermediate processed files
├── output/
│   ├── model_results.csv              # Summary metrics for all models
│   ├── detailed_results.csv           # Detailed evaluation results
│   └── model_comparison.png           # Performance comparison chart
└── requirements.txt                    # Python dependencies
```

## Setup Instructions

### 1. Environment Setup

```bash
# Create virtual environment
python -m venv .venv

# Activate virtual environment
source .venv/bin/activate  # On macOS/Linux
# OR
.venv\Scripts\activate     # On Windows

# Install dependencies
pip install -r requirements.txt
```

### 2. Download Dataset

Download the MIND dataset from Kaggle:
- Dataset URL: https://www.kaggle.com/datasets/arashnic/mind-news-dataset/data
- Place `MINDsmall_train.zip` and `MINDsmall_dev.zip` in the `data/` folder
- **Note:** The notebooks will automatically extract these files

### 3. Run Notebooks

Execute notebooks in order:

1. **MIND_Dataset_Exploration.ipynb** (Optional but recommended)
   - Performs exploratory data analysis
   - Generates visualizations and insights
   - Runtime: ~5 minutes

2. **MIND_Model_Implementation.ipynb** (Required)
   - Implements all 5 recommendation models
   - Evaluates models using NDCG@K, MRR, Precision@K, Recall@K
   - Generates comparison results and visualizations
   - Runtime: ~5-10 minutes

## Key Results

| Model | NDCG@10 | Precision@10 | Recall@10 | MRR |
|-------|---------|--------------|-----------|-----|
| Most Popular Baseline | 0.000153 | 0.000104 | 0.000361 | 0.000791 |
| ALS | 0.000120 | 0.000070 | 0.000289 | 0.000624 |
| **Item-CF** | **0.001483** | **0.000754** | **0.002263** | **0.002959** |
| Content-Based | 0.000733 | 0.000352 | 0.001236 | 0.001328 |
| **Hybrid** | **0.001483** | **0.000754** | **0.002263** | 0.002849 |

**Key Findings:**
- Item-based Collaborative Filtering achieved **869% improvement** in NDCG@10 over baseline
- Hybrid model matches CF performance while providing robustness for cold-start users
- ALS failed due to 75.5% of users requiring fallback to baseline (cold-start issues)
- Content-Based filtering showed moderate success (+379% NDCG@10)

## Dependencies

Core libraries:
- Python 3.13+
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- scipy
- implicit (for ALS)
- tqdm

See `requirements.txt` for complete list with versions.

## Dataset Information

**MIND (Microsoft News Dataset) - Small Version:**
- ~5,000 users
- ~42,000 news articles
- 7-day interaction period
- 99.99% sparsity
- 6% click-through rate

**Train/Test Split:**
- Training: First 5 days (temporal)
- Testing: Last 2 days (29,828 test users)

## Evaluation Metrics

- **NDCG@K** (K=5,10,20): Normalized Discounted Cumulative Gain
- **MRR**: Mean Reciprocal Rank
- **Precision@K**: Fraction of relevant recommendations
- **Recall@K**: Fraction of relevant items captured

## Report

The final report (`VaishnaviKamdi_AdvML_HW2_Report.pdf`) provides:
- Detailed methodology
- Results and discussion
- Model comparison analysis

## Contact

**Vaishnavi Kamdi**  
Email: v.kamdi@gwu.edu 
George Washington University

## References

1. Wu, F. et al. (2020). MIND: A Large-scale Dataset for News Recommendation. ACL 2020.
2. Koren, Y., Bell, R., & Volinsky, C. (2009). Matrix Factorization Techniques for Recommender Systems. IEEE Computer, 42(8).
3. Sarwar, B. et al. (2001). Item-based Collaborative Filtering Recommendation Algorithms. WWW 2001.
