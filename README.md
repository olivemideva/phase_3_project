# Keeping IBM Talent : Insights into Employee Retention

## Overview
This project aims to help IBM understand why employees leave the company and how to improve employee retention. By analyzing employee data, we identified key factors that influence whether an employee stays or leaves. We used simple machine learning methods to find the most important reasons for employee turnover. The project includes clear visualizations to illustrate our findings. Based on this analysis, we provide practical recommendations to help IBM keep its employees happy and reduce turnover.

## Business Understanding

### Project Objective
The main objective of this project is to help IBM reduce employee turnover by identifying the key factors that lead to employees leaving the company. By understanding these factors, IBM can implement targeted strategies to improve employee satisfaction and retention, ultimately leading to a more stable and productive workforce.

### Business Problem
IBM faces a high turnover rate, which is costly and disrupts productivity. The challenge is to pinpoint why employees leave and provide actionable recommendations to improve retention.

 ### Stakeholders
The primary stakeholders:
* HR department at IBM - interested in understanding employee turnover to develop better retention strategies. 
* Executives - concerned with the overall performance and stability of the company, which can be affected by high turnover rates. 
* Team managers - want to maintain a stable and motivated team to ensure productivity and morale.

## Data Understanding

### Dataset

The dataset is sourced from Kaggle and it  provides valuable employee information from IBM. The dataset captures diverse employee attributes and work-related factors, including demographic details, job specifics, and satisfaction metrics. It also includes indicators of employee turnover, providing a comprehensive view of organizational dynamics. With a mix of numerical and categorical variables, the dataset offers opportunities to explore patterns influencing employee attrition and organizational outcomes.
[My Dataset](https://www.kaggle.com/datasets/uniabhi/ibm-hr-analytics-employee-attrition-performance)

### Data Analysis

Here we prepared the dataset by encoding categorical variables and addressing class imbalance using SMOTE. In feature selection, we treated employee attrition as the target variable, while all other variables were considered as features. This approach helped us identify the most relevant features for predicting employee attrition while excluding the target variable from the feature selection process. 

### Class imbalance

![image](https://github.com/olivemideva/phase_3_project/blob/main/Images/Screenshot%202024-06-07%20120436.png).

The above visualization shows there's class imbalance in the dataset with Yes as minority and No as majority

### Checking for outliers

![image](https://github.com/olivemideva/phase_3_project/blob/main/Images/Screenshot%202024-06-07%20120759.png).

The dataset had outliers that weren't removed because that could affect the accuracy because they are important values needed for the dataset. Removing values from the columns 'TotalWorkingYears' and 'YearsAtCompany' will lead to loss of valuable information.

### Pair plot

![image](https://github.com/olivemideva/phase_3_project/blob/main/Images/Screenshot%202024-06-07%20120825.png).

The above explores the relationships between pairs of numerical features and attrition.

### Bar plot

![image](https://github.com/olivemideva/phase_3_project/blob/main/Images/Screenshot%202024-06-07%20120839.png).

The above helps to see how categorical features like BusinessTravel, Department, and EducationField vary across the target variable.

## Modelling

In our modeling phase, we tried out three different approaches: Decision Trees as the baseline model, Random Forests, and a tuned version of the Random Forest. We wanted to see which one could best predict whether an employee would stay or leave the company.

### Decision Tree

In our modeling phase, we tried out three different approaches: Decision Trees as the baseline model, Random Forests, and a tuned version of the Random Forest. We wanted to see which one could best predict whether an employee would stay or leave the company.

### Random Forest

Then, we tried the Random Forest, hoping it would do better. It did improve the accuracy to around 87%, which was good. We also looked at which factors were most important in predicting whether an employee would leave.

### Tuned Model

After that, we decided to make the Random Forest even better by fine-tuning it. This process helped us adjust the model to be even more accurate, up to about 92%. 

## Evaluation

In the evaluation stage, we looked at how well each model performed. The tuned Random Forest came out on top, showing it could predict employee turnover pretty well. Overall, these steps helped us understand our data better and build models that could predict employee turnover more accurately.

### Confusion matrix

![image](https://github.com/olivemideva/phase_3_project/blob/main/Images/Screenshot%202024-06-07%20025633.png).

* True Negatives (TN): 237
* True Positives (TP): 218
* False Negatives (FN): 26
* False Positives (FP): 13
This indicates that the model correctly identified 237 instances where employees stayed and 218 instances where employees left. It incorrectly identified 26 employees who left as those who stayed (false negatives) and 13 employees who stayed as those who left (false positives). The relatively lower number of false negatives compared to the previous models shows that the model is effectively identifying employees at risk of leaving, which is crucial for retention efforts.

### ROC Curve

![image](https://github.com/olivemideva/phase_3_project/blob/main/Images/Screenshot%202024-06-07%20025710.png).

With an AUC (Area Under the Curve) of 0.97, the ROC curve demonstrates excellent discriminative ability. It ascends steeply on the left, indicating that the True Positive Rate increases rapidly with minimal False Positive Rate, reflecting the model's ability to correctly identify positive cases while keeping false alarms low. However, the curve then sharply moves towards the upper-right corner, it implies a sudden increase in the False Positive Rate, possibly suggesting a threshold where the model becomes more liberal in classifying cases as positive. Despite this sudden rise, the overall AUC value of 0.97 signifies strong predictive performance and effective discrimination between positive and negative cases. This high AUC reflects the model's strong performance and reliability in identifying employees at risk of leaving.

### Feature against Importance tuned model

![image](https://github.com/olivemideva/phase_3_project/blob/main/Images/Screenshot%202024-06-07%20024241.png).

This plot shows which columns were given priority or rather have high importance in making the model, therefore these columns have high impact on the target column.

## Recommendations

### Model Recommendation
Based on the evaluation of three models—Decision Tree Classifier, Random Forest Classifier, and Random Forest Classifier with SMOTE and Hyperparameter Tuning—the Random Forest Classifier with SMOTE and Hyperparameter Tuning is recommended. This model achieved the highest accuracy of 92.1% and demonstrated balanced precision and recall for the minority class (employees likely to leave), with both metrics around 92%. In comparison, the Decision Tree Classifier had lower accuracy (78.2%) and poor recall for the minority class (18%), while the untuned Random Forest Classifier, despite higher accuracy (87.4%), had a very low recall (8%) for the minority class. The chosen model effectively handles class imbalance through SMOTE and benefits from optimized hyperparameters, making it the most reliable for identifying at-risk employees and informing retention strategies.

### Recommendations to stakeholder

Based on the feature importance analysis, several recommendations can be made to improve employee retention:

1. Focus on Stock Option Programs: Companies should consider enhancing or introducing stock option programs to incentivize employees to stay with the organization longer.
2. Address Job Satisfaction and Involvement: Employers should prioritize initiatives aimed at improving job satisfaction levels, such as recognizing employee achievements, providing opportunities for career advancement, and fostering a positive work environment that promotes engagement.
3. Consider Marital Status: Employers could explore benefits tailored to married employees, such as family-friendly policies or support programs to help balance work and personal life.
4. Promote Diversity and Inclusion: Organizations should foster an inclusive environment where employees from diverse backgrounds feel valued, respected, and supported. Implement diversity training, establish affinity groups, and create opportunities for cross-cultural collaboration.
5. Enhance Training and Development Opportunities: Investing in training programs, skill development workshops, and educational opportunities can demonstrate a commitment to employees' growth and encourage them to remain with the organization.
6. Address Work-Life Balance: Employers should strive to promote work-life balance by offering flexible work arrangements, implementing policies to prevent overwork, and encouraging employees to take regular breaks to recharge.
7. Address Overtime: Employers should monitor and manage workload distribution effectively to prevent employee burnout and dissatisfaction associated with excessive overtime.
8. Consider Role Satisfaction: Employers should tailor retention strategies to address the unique needs and challenges faced by employees in different roles.

## Contact Info
Olive Mideva Muloma
[My LinkedIn](https://www.linkedin.com/in/olive-mideva-ab312921b/)
