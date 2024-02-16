# ml_classifiers_comparison

This program compares the accuracy, training time, test time, and memory usage of the three supervised machine learning models used for classification on the iris dataset:

* Logistic regression
* K Nearest Neighbor
* Support vector machine

[Click here](https://github.com/yuzom/ml_classifiers_comparison/blob/main/ml_classifiers_comparison.ipynb) to see the code in action.

Here are the results:

| Model             | Accuracy | Training Time | Test Time | Max Memory Usage |
|-------------------|----------|---------------|-----------|------------------|
| SVM               | 1.000000 | 0.104072      | 0.000570  | 0.078125         |
| LogReg_Optimized  | 0.977778 | 0.208270      | 0.000403  | 0.593750         |
| KNN               | 0.977778 | 0.107184      | 0.008387  | 0.218750         |
| KNN_Optimized     | 0.977778 | 0.147413      | 0.002052  | 0.093750         |
| SVM_Optimized     | 0.977778 | 0.143163      | 0.000422  | 0.031250         |
| LogReg            | 0.933333 | 0.105661      | 0.000412  | 0.546875         |

We run a default model and an optimized model for each machine learning algorithm. The optimized models use grid search to find the most optimal hyper parameters.

It may be surprising that the default models are on par with or outperform the optimized models.

This is because the optimized models split the training dataset further into internal training and validation datasets to optimize their hyper parameters, meaning they have less training data to work with through each training and cross validation cycle compared to the default model. This is observed for small datasets like the iris dataset (N=150) that we use here.

Therefore, we conclude that for the iris dataset, it is not worth running hyper parameter optimization. Let's rank the performance of each model:
* For accuracy: SVM > KNN > LogReg
* For training time: SVM > LogReg > KNN
* For memory usage: SVM > KNN > LogReg

You may find that changing the random_state variable when we split the dataset into training and test will change the model accuracies. This shows again that performance is sensitive to which datapoints get split into training and test for small sample sizes.


**(C) 2024 Yuzo Makitani** This repository is released under the [GNU GPLv3.0 or later](https://www.gnu.org/licenses/).
