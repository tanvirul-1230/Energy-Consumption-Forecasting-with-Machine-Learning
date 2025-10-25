Energy Consumption Forecasting with Machine Learning

This project builds a time-series machine learning model to predict hourly energy consumption. It demonstrates how to combine operational data (energy demand) with external IT data (weather) to create a highly accurate forecast.

The model trains on historical data from the AEP grid and weather data from Indianapolis, using an XGBoost Regressor to predict future energy demand.

Final Model Performance

On a test set of 6 months of unseen data, the model achieved:

R-squared (R²): 0.97

Root Mean Squared Error (RMSE): ~414 MW (an error of ~2.7% against the average)

(This plot shows the model's predictions (red) vs. the actual energy demand (blue) for a 1-week period from the test set. Note the accurate tracking of peaks and troughs.)

Tech Stack

Python 3.10+

Pandas: For data loading, cleaning, and feature engineering.

NumPy: For numerical operations.

XGBoost: For the advanced gradient boosting model.

Scikit-learn: For model evaluation metrics.

Matplotlib: For plotting the results.

Project Structure

.
├── weather_data/
│   ├── temperature.csv
│   ├── humidity.csv
│   └── ... (other weather files)
├── AEP_hourly.csv
├── forecast.py
├── requirements.txt
├── README.md
└── .gitignore


How to Run This Project

1. Setup

Clone the repository:

git clone [your-repo-link]
cd [your-repo-name]


Create a virtual environment and install dependencies:

# Create venv
python -m venv .venv
# Activate
source .venv/bin/activate  # (or .\venv\Scripts\activate on Windows)
# Install libraries
pip install -r requirements.txt


2. Get the Data

You will need to download the two datasets for this project.

AEP Energy Data:

Source: Kaggle: AEP Hourly Energy Consumption

Action: Download AEP_hourly.csv and place it in the root of the project folder.

Weather Data:

Source: Kaggle: Historical Hourly Weather Data 2012-2017

Action: Download the dataset, unzip it, and place the resulting CSV files (like temperature.csv, humidity.csv, etc.) into a folder named weather_data.

3. Run the Model

Once your data is in place, simply run the main script:

python forecast.py


The script will:

Load and clean both datasets.

Merge them by their datetime index.

Engineer time-based, lag, and rolling features.

Train the XGBoost model.

Print the final evaluation metrics (RMSE and R²) to the console.

Save the prediction plot as prediction_plot.png in the project folder.
