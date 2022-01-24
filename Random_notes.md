### RNN
Gradient based methods learn a parameter's value by understanding how a small change in the parameter's value will affect the network's output. If a change in the parameter's value causes very small change in the network's output - the network just can't learn the parameter effectively, which is a problem.

This is exactly what's happening in the vanishing gradient problem -- the gradients of the network's output with respect to the parameters in the early layers become extremely small. That's a fancy way of saying that even a large change in the value of parameters for the early layers doesn't have a big effect on the output.

Certain activation functions, like the sigmoid function, squishes a large input space into a small input space between 0 and 1. Therefore, a large change in the input of the sigmoid function will cause a small change in the output. Hence, the derivative becomes small.

- However, when n hidden layers use an activation like the sigmoid function, n small derivatives are multiplied together. Thus, the gradient decreases exponentially as we propagate down to the initial layers.

- Solution:     
    The simplest solution is to use other activation functions, such as ReLU, which doesn’t cause a small derivative.

---
## Evaluation metrics

### Accuracy
- Not a good metric if imbalanced dataset. If data has most of the pts in one type of label.
- Accuracy cannot use probability score. If a model predicts 0.6 and other 0.9 for label 1 then 0.9 is better but this does not differentiate between them.

### Confusion matrix
- It cannot process probability scores.

**FP is also known as Type 1 error and FN is also called Type 2 error.** 

### $Precision = TP / (TP + FP)$    
- They care only about the positive class labels.     
- Spam email detection problem wherein classifying an email wrongly will cause you trouble as it can be very costly for the company. Here the False Positive should be observed keenly as it has more impact so Precision becomes important here.

### $Recall = TP / (TP + FN)$
- Say you are working on a cancer detection problem wherein not predicting cancer for a cancerous patient would be life-threatening for the patient. Here the False Negative should be observed keenly as it has more impact so Recall becomes important in this case.

## Clustering

- init centroid:
    - `Forgy`: randomly take k centroids
    - `random partition`: randomly assign each data point to a cluster, and then take avg to find centroids.
- `Elbow`: Cluster quality measure
    - `Distortion`: It is calculated as the average of the squared distances from the cluster centers of the respective clusters. (Typically, the Euclidean distance metric is used.)
    - `Inertia`: It is the sum of squared distances of samples to their closest cluster center.

- `Silhouette`: $(b-a)/max(a,b)$ for each point.
    - `+1 Score`: Near +1 Silhouette score indicates that the sample is far away from its neighboring cluster.
    - `0 Score`: 0 Silhouette score indicates that the sample is on or very close to the decision boundary separating two neighboring clusters.
    - `-1 Score`: -1 Silhouette score indicates that the samples have been assigned to the wrong clusters.

- `Dendrogram` is a diagram that shows the hierarchical relationship between objects. 
    - It is most commonly created as an output from hierarchical clustering. The main use of a dendrogram is to work out the best way to allocate objects to clusters.
    - The heights reflect the distance between the clusters as is shown below.
    - It is important to appreciate that the dendrogram is a summary of the distance matrix.

## Decision tree

### Gini
- Gini Index, unlike information gain, isn’t computationally intensive as it doesn’t involve the logarithm function used to calculate entropy in information gain
- `Gini`: $1 - sum(p_i^2)$

$P(Trading Volume=High): 7/10$

$P(Trading Volume=Low): 3/10$

    If (Trading Volume = High & Return = Up), probability = 4/7
    If (Trading Volume = High & Return = Down), probability = 3/7

    Gini index = 1 - ((4/7)^2 + (3/7)^2) = 0.49
---
    If (Trading Volume = Low & Return = Up), probability = 0
    If (Trading Volume = Low & Return = Down), probability = 3/3

    Gini index = 1 - ((0)^2 + (1)^2) = 0

### Entropy
- `Entropy`: $sum(-p_i * log(p_i))$

## Bias and Variance

- Underfitting = high bias
- Overfitting = low bias, high variance

$Bias = E[y^{'}-y]$     
$Variance = E[(E[y^{'}]-y^{'})^2]$