# CIC-IDS2017 Network Intrusion Detection

## Project Overview

This project focuses on detecting network intrusions using
Machine Learning and Deep Learning techniques.

The CIC-IDS2017 dataset was used to develop a binary
classification system capable of distinguishing between:

- Normal Traffic
- Attack Traffic

## Objectives

- Perform data preprocessing and cleaning.
- Analyze the CIC-IDS2017 dataset.
- Handle data quality issues and duplicate samples.
- Train multiple machine learning models.
- Compare traditional Machine Learning with Deep Learning.
- Evaluate models using multiple performance metrics.

## Dataset

The project uses a partially cleaned version of the CIC-IDS2017 dataset.

The dataset contains network traffic flow features and attack/normal
traffic labels.

Data quality checks and preprocessing were performed before model
training, including missing value analysis, duplicate detection,
suspicious value detection, and train-test overlap analysis.

For this project, the problem was formulated as a binary classification task:

- `0` → Normal Traffic
- `1` → Attack Traffic

The cleaned dataset used in this project is available on Kaggle:

**Kaggle Dataset:** [CIC-IDS2017 Cleaned Dataset](https://www.kaggle.com/code/huy47nguyennhat/data-cleaned-cicids2017/output)


## Data Preprocessing

The preprocessing pipeline includes:

- Missing value analysis
- Infinite value detection
- Duplicate detection
- Feature analysis
- Binary label encoding
- Train/Test splitting
- Feature scaling for the Neural Network
- Detection of suspicious corrupted values
- Detection of exact feature overlap between training and test sets
- Removal of exact train-test feature overlap from the test set

After removing the overlapping feature rows, the clean test set
contained 503,988 samples.

## Models

Four models were evaluated:

1. Decision Tree
2. Random Forest
3. XGBoost
4. MLP Neural Network

The first three models represent traditional Machine Learning
approaches, while the MLP represents the Deep Learning approach.

## Evaluation Metrics

The models were evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- PR-AUC
- Confusion Matrix

Since the main objective is intrusion detection, particular
attention was given to Recall and F1-score for the Attack class.

## Results

The models achieved very strong performance on the
clean test set.

| Model              | Accuracy | Precision | Recall | F1-Score | ROC-AUC | PR-AUC |
| ------------------ | -------: | --------: | -----: | -------: | ------: | -----: |
| Decision Tree      |   0.9989 |    0.9951 | 0.9986 |   0.9968 |  0.9990 | 0.9943 |
| Random Forest      |   0.9990 |    0.9953 | 0.9987 |   0.9970 |  0.9999 | 0.9988 |
| XGBoost            |   0.9988 |    0.9933 | 0.9995 |   0.9964 |  1.0000 | 0.9998 |
| MLP Neural Network |   0.9770 |    0.8851 | 0.9928 |   0.9359 |  0.9988 | 0.9945 |


### Results Discussion

The tree-based models achieved the strongest overall performance.
XGBoost achieved the highest Attack Recall (0.9995), ROC-AUC (1.0000),
and PR-AUC (0.9998), while Random Forest achieved the highest overall
F1-score (0.9970).

The MLP Neural Network also achieved a very high Attack Recall (0.9928),
but its overall performance was lower than the tree-based models,
particularly in Precision and F1-score.

## Confusion Matrices

The confusion matrices were also analyzed to evaluate
False Positives and False Negatives.

For intrusion detection, False Negatives are particularly
important because they represent attacks that were incorrectly
classified as normal traffic.

## Feature Importance

Feature importance analysis was performed using the Random Forest
model.

The most important features included:

- Packet Length Variance
- Average Packet Size
- Bwd Packet Length Std
- Max Packet Length
- Packet Length Std
- Destination Port
- Packet Length Mean
- Bwd Packet Length Mean
- Fwd Packet Length Mean
- Init_Win_bytes_forward
- Init_Win_bytes_backward


## Deep Learning

A Multi-Layer Perceptron (MLP) neural network was developed
using TensorFlow/Keras.

The architecture consists of:

- Dense layer: 128 neurons
- Dropout: 0.3
- Dense layer: 64 neurons
- Dropout: 0.3
- Dense layer: 32 neurons
- Output layer: Sigmoid

The MLP was trained using the scaled feature set.

## Key Findings

- Tree-based Machine Learning models achieved excellent performance
  on the CIC-IDS2017 binary classification task.
- XGBoost achieved the highest ROC-AUC and PR-AUC among the evaluated models.
- Random Forest also achieved near-perfect classification performance.
- The MLP achieved strong Attack recall but had lower precision and
  overall performance compared with the tree-based models.
- The results demonstrate the effectiveness of tree-based models
  for tabular network-flow intrusion detection data.

## Limitations

- The evaluation is based on the CIC-IDS2017 dataset and may not
  fully represent real-world network traffic.
- The project focuses on binary classification rather than
  detailed multiclass attack classification.
- Dataset-specific characteristics may contribute to the very
  high model performance.
- Further validation on independent datasets would be required
  to assess real-world generalization.

## Future Work

Possible future improvements include:

- Multiclass attack classification
- Evaluation on additional intrusion detection datasets
- Hyperparameter optimization
- Explainable AI techniques
- More advanced Deep Learning architectures
- Real-time network intrusion detection


## Authors

Rahma Abdelaziz Omar

Communication Systems Engineering  
Benha National University

## Supervision

Dr. Heidi Badr  
Dr. Ahmed Farouk

Electronics Research Institute (ERI)

## License

This project is intended for academic and educational purposes.
