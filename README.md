# Product-Demand-Prediction-Project
#  Product Demand Prediction using Decision Tree Regressor

This project focuses on predicting the weekly number of orders (`num_orders`) for food products using pricing features such as `checkout_price` and `base_price`. It includes data loading, exploration, visualization, model training using a Decision Tree Regressor, and performance evaluation.

---

## 📂 Dataset Details

- **Source**: [Weekly Demand Data.csv](https://raw.githubusercontent.com/SatvikPraveen/Food-Forecasting-Analysis-Tableau/main/Weekly%20Demand%20Data.csv)
- **Description**: Contains weekly demand and pricing data for various food products.

---

## Procedure

```python
import pandas as pd
import numpy as np
import plotly.express as px
import seaborn as sns
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.tree import DecisionTreeRegressor
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score

## 📥 Data Loading & Exploration 
# Load dataset
data = pd.read_csv("https://raw.githubusercontent.com/SatvikPraveen/Food-Forecasting-Analysis-Tableau/main/Weekly%20Demand%20Data.csv")

# Display first 5 rows
print(data.head())

# Dataset shape
print("Shape of the dataset:", data.shape)

# Check for missing values
print("Missing values in each column:\n", data.isnull().sum())

# Scatter plot - num_orders vs checkout_price
fig = px.scatter(data, x="num_orders", y="checkout_price", size="num_orders", title="Orders vs Checkout Price")
fig.show()

# Correlation matrix and heatmap
print("Correlation Matrix:\n", data.corr())
correlations = data.corr(method='pearson')
plt.figure(figsize=(15, 12))
sns.heatmap(correlations, cmap="coolwarm", annot=True)
plt.title("Heatmap of Correlations")
plt.show()

##🧠 Model Building
# Predict on test set
ypred = model.predict(xtest)

# Evaluation metrics
print("Mean Absolute Error:", mean_absolute_error(ytest, ypred))
print("Mean Squared Error:", mean_squared_error(ytest, ypred))
print("R^2 Score:", r2_score(ytest, ypred))
