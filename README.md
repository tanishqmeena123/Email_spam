# 📱 Email Spam Classification

An end-to-end Machine Learning and Natural Language Processing (NLP) project designed to automatically detect and filter unsolicited spam email messages with high precision.

## 📑 Table of Contents
* [Project Overview](#project-overview)
* [Dataset](#dataset)
* [Project Pipeline](#project-pipeline)
* [Model Performance](#model-performance)
* [Technologies Used](#technologies-used)
* [Installation & Usage](#installation--usage)

---

## 🎯 Project Overview
Spam messages account for a significant portion of global email traffic, posing security risks and degrading the user experience. This project tackles the problem by building a robust text classifier. The primary goal was to maximize **Precision** to ensure that legitimate messages (Ham) are never accidentally sent to the spam folder (zero False Positives).

## 📊 Dataset
The dataset used is `spam.csv`, which contains 5,572 email messages tagged according to being ham (legitimate) or spam.

* **Initial Shape:** `(5572, 5)`
* **Encoding:** `latin-1`
* **Class Distribution:** * Ham: ~87%
  * Spam: ~13%
* **Note:** The dataset contains extreme class imbalance, which was handled carefully during the train-test split (stratification) and model evaluation.

---

## 🔄 Project Pipeline

### 1. Data Cleaning
* Dropped redundant columns (`Unnamed: 2`, `Unnamed: 3`, `Unnamed: 4`) containing mostly `NaN` values.
* Renamed columns from `v1` and `v2` to `Target` and `Text` for better readability.
* Identified and removed duplicate entries to prevent model overfitting.

### 2. Exploratory Data Analysis (EDA)
* Analyzed the distribution of the target variable.
* Investigated message length correlations (email messages tend to be significantly longer than Ham messages).
* Generated Word Clouds to identify high-frequency words in both classes (e.g., "FREE", "WIN", "CALL" for spam).

### 3. Text Preprocessing (NLP)
* **Lowercasing:** Standardized all text.
* **Tokenization:** Split messages into individual words.
* **Special Character & Stopword Removal:** Filtered out punctuation and common English stopwords using `nltk`.
* **Stemming:** Reduced words to their root form using `PorterStemmer` (e.g., "calling" -> "call").

### 4. Feature Engineering
* Converted the cleaned text data into numerical vectors using **TF-IDF Vectorization** (Term Frequency-Inverse Document Frequency) to weigh the importance of specific words across the corpus.

### 5. Model Building
Trained and evaluated multiple classification algorithms:
* Multinomial Naive Bayes
* Support Vector Machine (SVM)
* Random Forest
* Logistic Regression

---

## 🏆 Model Performance

The **Multinomial Naive Bayes** classifier was selected as the final model due to its perfect precision score, which is the most critical metric for a spam filter.

| Model | Accuracy | Precision | Recall | F1-Score |
| :--- | :--- | :--- | :--- | :--- |
| **Multinomial Naive Bayes** | **97.2%** | **100.0%** | **80.3%** | **89.1%** |
| Support Vector Machine | 98.1% | 97.4% | 85.2% | 90.9% |
| Random Forest | 96.8% | 98.2% | 76.5% | 86.0% |
| Logistic Regression | 95.1% | 96.0% | 68.0% | 79.6% |

> **Key Finding:** While SVM had slightly higher overall accuracy, MultinomialNB was chosen because a Precision of 100% guarantees zero false positives (no real messages marked as spam).

---

## 💻 Technologies Used
* **Language:** Python
* **Data Manipulation:** `pandas`, `numpy`
* **Data Visualization:** `matplotlib`, `seaborn`
* **Natural Language Processing:** `nltk` (Natural Language Toolkit)
* **Machine Learning:** `scikit-learn`
* **Environment:** Jupyter Notebook




