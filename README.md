# Health-Care-Provider-Fraud-Prediction using Decision-Tree-Classifiers
 I will be exploring Decision Tree Classifiers using Health Provider Fraud Dataset

![alt_text](https://gaps.cornell.edu/sites/gaps.cornell.edu/files/shared/images/Decision-Tree-4.gif)

### Data set

The data file can be found on repository with name health_provider_fraud.csv.  

These data were re-configured from a dataset collected for the purpose of detecting Health care Provider Fraud. Total Medicare spending increases exponentially due to frauds in Medicare claims. Healthcare fraud involves health care providers, physicians, patients, and beneficiaries acting intandum to construct fraudulent claims.

The goal is to "predict potentially fraudulent providers" from summary statistics of their filed healthcare claims. 


__Features__  
The features are aggregate statistics computed as either the mean or the sum.
For the following features, the column is indicative of the average value for the provider's claims:  
* InscClaimAmtReimbursed  
* DeductibleAmtPaid
* NoOfMonths_PartACov
* NoOfMonths_PartBCov
* IPAnnualReimbursementAmt
* IPAnnualDeductibleAmt
* OPAnnualReimbursementAmt
* OPAnnualDeductibleAmt
* NumPhysiciansSeen
* NumProcedures
* NumDiagnosisClaims
* Age
 
For the following features, the column is indicative of the total number among the provider's claims:  
* ChronicCond_Alzheimer  
* ChronicCond_Heartfailure  
* ChronicCond_KidneyDisease  
* ChronicCond_Cancer  
* ChronicCond_ObstrPulmonary  
* ChronicCond_Depression  
* ChronicCond_Diabetes  
* ChronicCond_IschemicHeart  
* ChronicCond_Osteoporasis  
* ChronicCond_rheumatoidarthritis  
* ChronicCond_stroke  
* RenalDiseaseIndicator  

These data were amalagmated from the [HEALTHCARE PROVIDER FRAUD DETECTION ANALYSIS](https://www.kaggle.com/rohitrox/healthcare-provider-fraud-detection-analysis) data set on Kaggle.

### please check the notebook for complete analysis and predictions form summary statistics

### Results:
I have initially selected a model based on manual hyperparamters and then tried GridSearchCV to get the best model.

### Test Results: My model

* Mean accuracy:0.9279461279461281

* ROC AUC: 0.834766504173353 

* PRC AUC: 0.57410142068317 

* PSS: 0.4142 

* F1 Score 0.5301

* TN: 960, FP:21, FN:57,TP:44


__base Model Decision Tree__

![model_best](https://user-images.githubusercontent.com/46058709/73575184-40424480-443d-11ea-9464-d106d7a3eb99.png)


### Test Results : GridSearch

* Mean accuracy0.9288720538720538 

* ROC AUC: 0.8548359423098272 

* PRC AUC: 0.5993878969277282 

* PSS: 0.5379 

* F1 Score 0.6196

* TN: 955, FP:26, FN:44,TP:57

__Grid search Decision Tree__
![gsearch](https://user-images.githubusercontent.com/46058709/73575090-ff4a3000-443c-11ea-8ce0-8f9ce94879a4.png)

I have Improvement in my Test results For Grid Search. Eventhough the values did not change a lot, it can be seen that the values have improved.

Both ROC AUC and PRC AUC have improved for Grid Search.
as the classifier is predicting more points that belong to positves,we are getting better results for grid search.It is same with PRC AUC value too.
True Negatives are pretty close for both the models. The error values are reduced for grid search.
F1 score also improved for Grid Search.

From these results we can see that Grid search is doing really well with our data, but in our data there are more negative examples than the positive ones, that is the reason we have relatively low PRC AUC values compared to ROC AUC. Prediction of negative values was way higher than that of positive values prediction.

On whole I still would like to see values of PRC AUC close to 1. But comparing the both models, i can say that GridSearch gives me better results, than my selected model.

I have not used proper hyperparameters in my inital model,I think Having better Hyperparameters gave me better results.
I even observed that different splits in training data generated very different trees. And I see that Decision tree is not very accurate for this particular problem.


### Comparing the best model from the grid search to the one I have choosen 

It can be clearly seen that my Initial model generates a DecisionTree that is Unbalanced, but is giving me pretty good results.I have used Max_depth= 5 for my model, in the Grid Search I see that I get to have a max_deph to be 4, so the splitting of the tree is done accordingly.

For my model, I have selected Gini Impurity, In the Grid Search entropy was taken as the Criterian.

First two levels of my model, has better balance, but after that they are handling much more exceptions.Gini Scores are more diverse for my model, so from just the visualization i think we need better structure.

Coming to the Grid Search, we have entropy values, which are again not very close, they are diverse but we get to see better results as entropy closes to zero in most of the cases, which makes the prediction easier.Certainly Model can perform better.

In both the Model Feature 2(NumProcedures) was selected to have highest Feature Importance than other Feaures, that can seen in both the trees as This feature was selected at early level of the tree. Just by looking at the split levels, we can get an idea of feaures chosen at that particular level will be having higher importance than other fetures.



### General References
* [Guide to Jupyter](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Python Built-in Functions](https://docs.python.org/3/library/functions.html)
* [Python Data Structures](https://docs.python.org/3/tutorial/datastructures.html)
* [Numpy Reference](https://docs.scipy.org/doc/numpy/reference/index.html)
* [Numpy Cheat Sheet](https://s3.amazonaws.com/assets.datacamp.com/blog_assets/Numpy_Python_Cheat_Sheet.pdf)
* [Summary of matplotlib](https://matplotlib.org/3.1.1/api/pyplot_summary.html)
* [DataCamp: Matplotlib](https://www.datacamp.com/community/tutorials/matplotlib-tutorial-python?utm_source=adwords_ppc&utm_campaignid=1565261270&utm_adgroupid=67750485268&utm_device=c&utm_keyword=&utm_matchtype=b&utm_network=g&utm_adpostion=1t1&utm_creative=332661264365&utm_targetid=aud-299261629574:dsa-473406587955&utm_loc_interest_ms=&utm_loc_physical_ms=9026223&gclid=CjwKCAjw_uDsBRAMEiwAaFiHa8xhgCsO9wVcuZPGjAyVGTitb_-fxYtkBLkQ4E_GjSCZFVCqYCGkphoCjucQAvD_BwE)
* [Pandas DataFrames](https://urldefense.proofpoint.com/v2/url?u=https-3A__pandas.pydata.org_pandas-2Ddocs_stable_reference_api_pandas.DataFrame.html&d=DwMD-g&c=qKdtBuuu6dQK9MsRUVJ2DPXW6oayO8fu4TfEHS8sGNk&r=9ngmsG8rSmDSS-O0b_V0gP-nN_33Vr52qbY3KXuDY5k&m=mcOOc8D0knaNNmmnTEo_F_WmT4j6_nUSL_yoPmGlLWQ&s=h7hQjqucR7tZyfZXxnoy3iitIr32YlrqiFyPATkW3lw&e=)
* [Sci-kit Learn Linear Models](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.linear_model)
* [Sci-kit Learn Ensemble Models](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.ensemble)
* [Sci-kit Learn Metrics](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.metrics)
* [Sci-kit Learn Model Selection](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.model_selection)
* [Sci-kit Learn Pipelines](https://scikit-learn.org/stable/modules/generated/sklearn.pipeline.Pipeline.html)
* [Sci-kit Learn Preprocessing](https://scikit-learn.org/stable/modules/classes.html#module-sklearn.preprocessing)
