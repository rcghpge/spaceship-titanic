<p align="center">
  <img src="UTA-DataScience-Logo.png" />
</p>

<!-- Use this div with the custom class around your text -->
<div class="custom-text">

## Kaggle Challenge: Metastatic Cancer Diagnosis Prediction. Building and Benchmarking ML Models

This repository holds an attempt to apply machine learning to metastatic cancer diagnosis predictions using data from the WiDS Datathon 2024 Challenge #1 Kaggle challenge that ran from 1/9/2024 - 3/1/2024.

*Kaggle Page Link: https://www.kaggle.com/competitions/widsdatathon2024-challenge1/overview.*

## Overview

There's a challenge to figure out if certain people are less likely to get an early diagnosis of metastatic cancer due to factors like their age or where they live. The goal is to use a machine learning model, which is like a smart computer program, to predict if someone will be diagnosed with this type of cancer within 90 days of their first medical screening. The model looks at different pieces of information (features) about patients, both numbers and categories, to make its predictions. It's a test to see if the model can use this data to accurately guess who gets diagnosed quickly.
This is a breakdown that tested three different models to see how well they could do this. Two models were almost equally good, predicting cancer diagnosis within 90 days about 81% of the time. However, the best score someone has achieved on this task on Kaggle is 82.1% accuracy. The main aim is to find patterns in patient data that help with early and fair treatment for everyone.

## Summary of Workdone

### Data

Imagine you have a big folder of health checkup forms from 2015 to 2018 for people getting tested for breast cancer. It's like a huge list with around 12,906 names on it. This list is saved in two files, kind of like Excel sheets, named train.csv and test.csv. The last part of each line in these sheets tells you if the person has cancer or not. The whole folder was about 15MB at first, but after adding some more stuff I did, it's now around 80MB—pretty hefty. I tried to organize this folder in two different ways using some computer tools (Pandas and Scikit-Learn), but it got a bit messy. That will need to be sorted out. Hope that makes sense

#### Preprocessing / Clean up

* Exploratory data analysis, data preprocessing, data cleaning, data visualization, and feature engineering on training and test data

#### Data Visualization
<p>
Benchmarking is like comparing video games to see which one is better. I played the games (trained the models) to see how they perform. It was a bit tough but really cool to learn from. I didn't get to the part where you make the game run perfectly (fine-tuning the models) because it would have taken ages—like over 100 hours! But even without that, I learned a lot about how each game works and gets better as you play (how models learn from data). 
</p>

##### XGBoost Learning Curve
<div><img src="https://github.com/rcghpge/metastatic-cancer-diagnosis-prediction/blob/main/images/XGBoost%20Model%20Learning%20Curve.png" with="450" height="450"></div>


##### Gradient Boosting Learning Curve
<div>
<img src="https://github.com/rcghpge/metastatic-cancer-diagnosis-prediction/blob/main/images/GBD%20Model%20Learning%20Curve.png" width="500" height="500">
</div>

### Problem Formulation

* How can machine learning be leveraged to aid in cancer research and treatment?
  * Pretrain a ML model that leverages AI & machine learning for cancer research, treatment, diagnosis, and prediction
  * Models
    * The 3 models I tested were XGBoost, Stochastic Gradient Descent, and Gradient Boosting. I settled on 2 final models.

### Training

  * Training was done in a Jupyter Notebook environment utlizing Ubuntu version 22.04 LTS. This was on a Dell Workstation Precision 5510 laptop.
  * Most of the training went smooth. However fine-tuning the selected model was taking over 3+ hours.
  * Deciding on which training and test sets from the data was straightforward when looking at the ROC curves and measuring for AUC as well as cross-validating model accuracy. I wanted to note that I ran into issues with data shape for the training and testing data.
  * My main issues here was prepocessing, fitting, and fine-tuning.
  * Some light hyperparamter fine-tuning was done. Though was crunched for time on project final submission.

### Performance Comparison

* All 3 models performed fairly well. The best performing model seemed to be Gradient Boosting. You can see below from the ROC curve graph. I wasn't happy with 81.01% accuracy and because of my issues with data shape, I believe this affected the peformance of the models. If I had more time on the project, I would have pushed for 85% to over 90% accuracy.

#### ROC Curve Graph

<p><div><img src="https://github.com/rcghpge/metastatic-cancer-diagnosis-prediction/blob/main/images/Pandas%20Training%20Data%20ROC%20AUC%20Curve.png" width="600" height="500"></div></p>

### Conclusions

* The Gradient Boosting model worked the best for me compared to the XGBoost and Stochastic Gradient Descent models. I would have liked to try out GPU training, testing, and fine-tuning to see if it is faster. Though I've read mostly TensorFlow utilizes GPU compute and also that Scikit-Learn libraries do not have support for GPU compute. Though I just getting into machine learning. The training on my machine was done on CPU and RAM memory.

* In the little time window I had before submitting my project for this class, I was browsing through the Kaggle challenge page. Other participants of the challenge I saw trained and tested over 20 models. The most popular model I noticed reading through the various approaches were CatBoost and utilizing Optuna for fine-tuning.

* My concluding thoughts are that there is a lot of work that can be done from this challenge. This project alone could stand for benchmarking. Hopefully this will be of some use to someone.

### Future Work

* I think the next thing I would do is look into why NO2 was so pronounced in my training data. See Heatmap section of Notebook #1. From a simple Google search, I found that the most prominent source of NO2 are internal combustion engines - motor vehicles. This may be worth looking into. Something else to look into is socioeconomic status. That feature came up as important while I was training, testing, and fine-tuning my models. Another contributor found the metastatic cancer diagnosis codes to be the strongest predictive feature in their model. This should also be looked into as well. Another feature that was a surprise to me white fine-tuning was geographical location feature. I don't know why but this came up as another predictive feature as i was training and fine-tuning. I did not fully look into the aggregrate of the data. There are many predictive features from the data that can be utilized for benchmarking in machine learning. For more context you can see other contributors notebooks on Kaggle to give you a better idea. I believe there are alot of studies and use cases in this challenge. Cancer, viruses (COVID-19 recently in 2020), public health studies. Benchmarking datasets, and ML models for practical applications. There are many use cases for this model.
  
## How to reproduce results

* To replicate my exact results:
   * Jupyter Notebooks: Do not run every cell in each notebook. For Notebook #1: import libraries and software packages, load and read in the training and testing data, one-hot encode the categorical features with Pandas and Scikit-Learn, make sure to drop columns that are not needed, run the cells that take care of null values. You are doing this for the training data and the testing data. But if you want you can choose to one-hot encode once for the training data and once for the testing data. For Notebook #2: This is my original model. I tried to make it easy to understand, but I ran into issues with data shape of the training and testing data. So Notebook #2 is the original model trained, fitted, and fine-tuned only on partial data mainly the Scikit-Learn training data. Model 1 notebook, you can use that as an original benchmarking model. In Notebook #3 I went back and trained, fitted, tested, and fine-tuned Model 2 on the aggregrate training data. Or at least I tried. The results are show there. Notebook #1 makes for a solid benchmark for building robust data for training and testing.
   * Windows, Mac users, VS Code, etc: You can probably take bits and pieces of Notebook #1, #2, and #3 for your usage purposes. There are many environments out there for machine learning. Some use Google Colab, Jupyter Notebooks, Ubuntu, VS Code. I noticed the hot trend in machine learning these days are VS Code and GPUs.

### Overview of files in repository

  * The repository has 2 folders images and notebooks. The notebooks folder contains the 3 notebooks below.
  * eda-preprocessing.ipynb: Notebook 1 for prepping aggregate data for ML training, fitting, testing, validation, and fine-tuning.
  * ml-inference-submission.ipynb: Notebook 2 for ML model training, testing, validation, selection, and submission of model predictions. Original model - Model 1.
  * ml-inference-submission2.ipynb: Notebook 3 for ML model training, testing, validation, selection, and submission of model predictions. Model 2.
  * README.md: Breakdown of Github repository and files.
  

  * Note: You can skip Notebook #1 and directly download the training and testing data from Kaggle and use Notebook #2 and #3 for model training, testing, exploration.


### Software Setup

* Software libraries and packages needed: Scikit-Learn, Numpy, Seaborn, Pandas, Matplotlib, Math, XGBoost, IPython, and tabulate.
* From the libraries you can import the specific packages listed at the top of each notebook that you will need. If your machine does not have it check online. Most if not all of them have documentation for installing on your machine.

* I came across a library called Imbalance Learn while I was preproccesing the training and testing data. Its a library for dealing with imbalance in datasets.
* See link: https://imbalanced-learn.org/stable/

### Data

* The original training and testing data can be downloaded from the Kaggle link above. Browse over to data, and you can download them from there. The main idea in preprocessing the data is that you are benchmarking numerical and categorical features for robust predictive binary classification in machine learning.

### Training

* The most imporant thing I learned during this challenge was having the correct training and testing data. From there you divide up your training and testing data. Training data is for training and validating the models. Once you have decided on the most optimal model and best parameters, fit, test, and fine-tune your final model with the best parameters to make your best predictions.

#### Performance Evaluation

* For performance evaluation, you can run multiple models in 1 go or 1 at a time. I chose 3 in 1 go and ended with the 2 best models I thought would give the best and most accurate prediction. Check the graphs and cross-validation accuracy scores to help on selecting a final model. Fine-tune your models for best results.

## Citations & Acknowledgements
* This Kaggle notebook was fairly helpful for me. Thanks Dee Dee. I also want to thank my professor Dr. Farbin and my graduate TA's Vineesha and Kunal for answering my questions throughout the semester.
* Kaggle challenge contributors:
* dee dee @ddosad Kaggle notebook: https://www.kaggle.com/code/ddosad/wids-data-exploration-ml-starter

 
If you found this project helpful. Feel free to connect with me. Just ping me here on Github or on socials. Cheers =)

</div>






