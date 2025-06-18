# CA-Housing-Price-Prediction

## Overview

This project analyzes California housing data sourced from Redfin.com to predict house prices accurately. It incorporates comprehensive data preparation, feature engineering, visualization, and advanced machine learning models to deliver precise predictions.

## Dataset Description

The dataset (`Data.csv`) contains over 45,000 records with 29 features. Key columns include:

* **PRICE**: Sale or listing price of the property.
* **CITY**: City where the property is located.
* **SQUARE FEET**: Size of the property.
* **PROPERTY TYPE**: Type of property (Single Family, Condo, etc.).
* **BEDS**: Number of bedrooms.
* **BATHS**: Number of bathrooms.
* **YEAR BUILT**: Year the property was built.
* **HOA/MONTH**: Monthly Homeowners Association fees (excluded due to high null values).
* **LOT SIZE**: Lot size of the property.

## Methodology

* **Data Cleaning**: Removed duplicates and outliers using the IQR method.
* **Feature Engineering**: Handled categorical variables (CITY, PROPERTY TYPE), conducted correlation analysis, and strategically selected and dropped features.
* **Visualization**: Created histograms, box plots, and scatter plots to explore feature relationships.
* **Machine Learning Models**:

  * Linear Regression (baseline)
  * Logistic Regression
  * Gradient Boosting Regression
  * Lasso Regression (with GridSearchCV tuning)
  * Neural Network (best-performing model)

## Results

* **Best Model**: Neural Network achieved the highest R² score of 0.799, outperforming other models.

## Instructions

### Setup

Clone the repository:

```
git clone https://github.com/username/CA-Housing-Price-Prediction.git
```

Install dependencies:

```
pip install -r requirements.txt
```

### Running Notebooks

Navigate to the notebooks directory and run 

code.ipynb

The requirement is to only submit one file for the code, but for better practice, I should break it into:
1. `01_EDA_and_Data_Cleaning.ipynb`
2. `02_Feature_Engineering.ipynb`
3. `03_Model_Training_and_Tuning.ipynb`
4. `04_Model_Evaluation.ipynb`

I separated them in the code file by using different sections, though. 

## Directory Structure

```
CA-Housing-Price-Prediction/
├── README.md
├── data/
│   └── Data.csv
├── notebooks/
│   ├── code.ipynb
├── reports/
│   ├── Project_Report.pdf
│   └── Slides.pptx
└── requirements.txt
```

## Learnings
One of the key takeaways from this project is that we learned the importance of distinguishing between numerical features and categorical features. At first, we included zip codes in our selected features because we believe that zip codes can provide a more detailed idea about how location affects housing prices. However, later, we found that our model takes the zipcode column as a numerical feature. We had two options either transform the zipcode column to a categorical feature or use the city column instead. After our experiment, using the city column makes more improvement of the model performance. The second takeaway we learned is that we need to find a balance between correlation and null values. From our finding in the heatmap, column ‘HOA/MONTH’ has a higher correlation value to the price column compared to other columns. However, when we run code to check for null values, this column has 34777 null values, which means 73.8% of this column is empty. We decided not to put this column into our selected features since the sample size will be much smaller after dropping null values. The last takeaway is that even though tuning the parameters can be very time-consuming, it is vital in improving the model's performance. No parameters or model can suit all datasets.


## References

* Data sourced from [Redfin.com](https://www.redfin.com/)
