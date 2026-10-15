# ⚽ Premier League Match Prediction

**Predicting English Premier League match outcomes using Machine Learning and Statistical Modeling.**

This project explores different approaches to predicting Premier League football matches using historical match data. It compares multiple machine learning classifiers and a statistical Poisson goals model to understand their strengths, limitations, and predictive performance.

The goal is not just to maximize accuracy, but also to evaluate how well each model distinguishes between **home wins, draws, and away wins**.

## 📌 Project Overview

Football match prediction is a challenging problem because match outcomes depend on many factors, including team strength, recent form, scoring patterns, and the inherent uncertainty of football.

In this project, I built a comparative prediction pipeline using historical Premier League results. The notebook covers data preparation, feature engineering, model training, evaluation, and visualization.

### Key objectives

- Explore and validate historical match data.
- Engineer features from previous matches while avoiding future-data leakage.
- Train and compare different predictive models.
- Evaluate models using multiple classification and probability metrics.
- Analyze the difficulty of predicting draws.
- Identify promising approaches for future improvements.

## 🤖 Models Compared

The project evaluates six approaches:

| Model | Description |
|---|---|
| **Dummy Classifier** | Baseline using historical class frequencies. |
| **Logistic Regression** | Linear classification model for three possible outcomes. |
| **Random Forest** | Ensemble of decision trees that captures nonlinear patterns. |
| **Extra Trees** | Randomized tree ensemble for comparison with Random Forest. |
| **Histogram-Based Gradient Boosting** | Boosting approach that learns patterns through sequential tree improvements. |
| **Poisson Goals Model** | Statistical approach that models home and away goals and derives match-outcome probabilities. |

## 📊 Model Performance

The models are evaluated on a chronological test set covering the 2019–2023 seasons. This provides a more realistic evaluation than randomly mixing older and newer matches.

| Model | Accuracy | Macro F1 | Log Loss ↓ |
|---|---:|---:|---:|
| Histogram Gradient Boosting | 51.68% | 0.3810 | **1.0039** |
| Poisson Goals | 51.63% | 0.3662 | 1.0055 |
| Random Forest | 49.05% | 0.4294 | 1.0246 |
| Extra Trees | 48.53% | **0.4499** | 1.0284 |
| Logistic Regression | 47.47% | 0.4437 | 1.0357 |
| Dummy Classifier | 44.42% | 0.2051 | 1.0708 |

*Results are from the notebook's current evaluation. They are not guarantees of future performance.*

### How to interpret the results

- **Highest accuracy:** Histogram Gradient Boosting.
- **Best macro F1:** Extra Trees, indicating the strongest overall balance across the three outcome classes among these models.
- **Lowest log loss:** Histogram Gradient Boosting, indicating the best probabilistic predictions according to this metric.
- **Main challenge:** Draw prediction remains difficult, highlighting the class imbalance and uncertainty present in football results.

No single metric tells the whole story. Accuracy measures the proportion of correct predictions, macro F1 gives equal weight to each outcome class, and log loss evaluates the quality of predicted probabilities.

## 🧰 Technologies Used

- **Python** — data processing and model development
- **Pandas & NumPy** — data manipulation and numerical operations
- **Scikit-learn** — preprocessing, machine learning models, and evaluation
- **Matplotlib & Seaborn** — data visualization
- **SciPy** — statistical distributions and Poisson-based calculations
- **Jupyter Notebook** — experimentation and documentation

## 📁 Project Structure

```text
premier-league-prediction/
├── PL_prediction_all_models.ipynb
├── premier-league-matches.csv
└── README.md
```

The CSV file is the dataset expected by the notebook. If it is not included in the repository, obtain it from the original data source and place it beside the notebook before running it.

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/zakariakarbi/premier-league-prediction.git
cd premier-league-prediction
```

### 2. Create a virtual environment (recommended)

```bash
python -m venv .venv
```

Activate it:

**Windows**

```bash
.venv\Scripts\activate
```

**Linux / macOS**

```bash
source .venv/bin/activate
```

### 3. Install the dependencies

```bash
pip install pandas numpy scikit-learn matplotlib seaborn scipy jupyter
```

### 4. Prepare the dataset

Make sure `premier-league-matches.csv` is available in the project directory, with the columns expected by the notebook, including:

- `Date`
- `Season_End_Year`
- `Home`
- `Away`
- `HomeGoals`
- `AwayGoals`
- `FTR`

The `FTR` column represents the full-time result: `H` for home win, `D` for draw, and `A` for away win.

### 5. Run the notebook

```bash
jupyter notebook PL_prediction_all_models.ipynb
```

Run the cells from top to bottom to reproduce the analysis, train the models, and inspect the evaluation results.

## 📏 Evaluation Methodology

To reduce the risk of overly optimistic results, the notebook uses a chronological training, validation, and testing workflow.

The comparison includes:

- **Accuracy:** Overall proportion of correct predictions.
- **Balanced accuracy:** Average recall across outcome classes.
- **Macro F1-score:** Equal-weighted F1 across home wins, draws, and away wins.
- **Log loss:** Measures the quality of predicted probabilities; lower is better.
- **Multiclass Brier score:** Measures probability prediction error; lower is better.
- **Confusion matrices:** Show which outcomes are most often confused.

The notebook also uses historical team-form features and preprocessing pipelines to help prevent information from future matches leaking into model training.

## ⚠️ Limitations

This project is an experimental study, not a betting system or a guarantee of match outcomes.

- Historical performance does not guarantee future performance.
- The dataset currently ends in May 2023, so the results do not establish performance on recent seasons.
- Team strength changes over time because of transfers, injuries, tactics, and managerial changes.
- Draws are inherently difficult to predict.
- The current feature set does not capture every factor that influences a match.
- Model performance can vary across different test periods.

Predicted probabilities should therefore be interpreted as model estimates, not certainties.

## 🔭 Future Improvements

Potential next steps include:

- Incorporating expected goals (xG), shots, possession, and other match statistics.
- Adding Elo ratings and dynamic team-strength estimates.
- Testing rolling-window evaluation across multiple seasons.
- Optimizing hyperparameters using validation data.
- Calibrating predicted probabilities.
- Comparing predicted probabilities with bookmaker odds as a separate research exercise.
- Building a small interactive dashboard for exploring predictions.

## 🎓 What This Project Demonstrates

This project provides practical experience with:

- Exploratory data analysis and data validation.
- Feature engineering for sequential sports data.
- Classification and statistical modeling.
- Avoiding data leakage through chronological evaluation.
- Comparing models using multiple evaluation metrics.
- Interpreting model performance and limitations.

## 👤 Author

**Zakaria Karbi**

Statistics, Econometrics & Actuarial Sciences student interested in Data Science, Machine Learning, and AI Engineering.

- GitHub: [@zakariakarbi](https://github.com/zakariakarbi)

---

*Built as a machine learning project to explore statistical modeling and predictive analytics in football.*

**If you find this project useful, consider giving the repository a ⭐!**
