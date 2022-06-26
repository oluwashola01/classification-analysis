<h2>Introduction</h2>
<p>This report summarizes the analysis work done on the classification_40 dataset for State Farm.</p>
<h2>Objectives</h2>
<p>To build two different models using Logistic regression and a non-glm model to correctly classify and predict if an observation belongs to the positive class (labeled 1).</p>
<h2>Strategy</h2>
<ul>
  <li>Performed exploratory data analysis/Feature Engineering</li>
<li>Model development</li>
<li>Evaluate the performance and choose the best model</li>
  </ul>
<h2>Background</h2>
<p>There is a case of imbalance between the two class labels with the positive class – 1 having 14.51% while the negative class – 0 class has 85.49% of the observations (records). To handle this case, three techniques were employed in creating datasets:</p>
  <li>Created a dataset where the number of observations from the majority class randomly (positive labels) selected is the same number of observations from the minority class (negative labels). 
<ul><li>Majority –- the class with a large number of observations (records)</li>
  <li>Minority –- the class has a low number of observations</li></ul>
This technique would help to have a balanced datasets where the observations are approximately evenly distributed to both classes.</li>
<li>Used the dataset with the imbalance situation – In this method, the dataset was used without redistribution of the observations. This allows for testing the performance of the models on the imbalanced dataset.</li>
<li>Performed oversampling to up-sample the minority class to have a close proportion of observations to the majority class</li>
<p>For each of the techniques used to create datasets, the datasets were further split into two, train and test.<br>
To avoid data leakage, the model trained on the training dataset was used to predict the missing observations for the test dataset used predict the probabilities for both glm algorithm and non-glm algorithm using Multiple Imputation by Chained Equations (MICE).</p>
<h2>Model Development</h2>
<ul><li>Feature Selection Process - Variables that are most important/relevant</li>
<li>GLM - Logistic regression: Recursive Feature Elimination (RFE) method was considered in selecting the most important features. The combination of variables with the lowest Akaike Information Criterion (AIC) metric was selected. This means that only the variables included are more likely to improve the model, any addition or removal of variables can reduce the quality of the model.</li>
<li>Non-GLM Models: Accuracy score and Area Under Curve (AUC) were used to determine the best features.</li></ul>
<h2>Model Implementation</h2>
<p>The model was trained on both balanced and imbalanced datasets, however, results for only the balanced model are reported due to system performance which would require a lot of time to evaluate the performance of non-glm models on the imbalanced datasets. </p>
<h2>Model Evaluation</h2>
<p>The following models were built and evaluated using Area Under Curve (AUC):
  <ul><li>Logistic regression </li>
<li>Decision Tree Model (CART)</li>
<li>Random Forest</li>
<li>Support Vector Machine</li>
 <li> XGBoost</li>
 <li>Stacking Model</li></ul></p>
 <h2> Observation - Technique I </h2>
<p>The Stacking model was the best amongst the non-glm models with an AUC score of 0.79 while the Logistic regression model has an AUC score of 0.69.</p>
<p>If there are resources, Stacking would learn from the weak performances of other algorithms used to train models and produce a better performance, and this will lead to producing a better result on the test dataset. Logistic regression though faster but does not have the capability of learning from other models compared to Stacking. This was obvious with the Stacking outperforming the Logistic regression with an AUC of approximately 0.1 </p>

<h2>Conclusion - Technique I</h2>
Stacking outperformed the Logistic regression in identifying the optimal features that are relevant in predicting if an observation belongs to the positive class. There is approximately 79% chance that the model when trained with Stacking will be able to distinguish between positive and negative classes when classifying an observation compared to approximately 69% chance when the model is trained with the Logistic regression.
