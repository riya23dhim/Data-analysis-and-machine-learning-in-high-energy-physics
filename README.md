# PID-at-BelleII-using-Machine-Learning
The Belle II experiment employs the information from six sub-detectors (SVD, CDC, TOP, ARICH, ECL, and KLM) to identify a particle (electron, muon, pion, kaon, proton, or deuteron). This thesis aims to Investigate different machine learning models to improve K/$\pi$ separation. The XGBoost model outperforms the standard method for particle identification employed at Belle II, as well as other machine-learning based methods with an AUC score of 0.966.
The Belle II experiment employs the information from six sub-detectors (SVD, CDC, TOP, ARICH, ECL, and KLM) to identify a particle (electron, muon, pion, kaon, proton, or deuteron). This thesis aims to Investigate different machine learning models to improve K/π separation. The XGBoost model outperforms the standard method for particle identification employed at Belle II, as well as other machine-learning based methods with an AUC score of 0.966.
# Likelihood Method
The standard approach for PID at Belle II  uses the likelihoods from each of the six detectors for the six hypotheses: e, μ, π, K, p, and d. To define a combined PID likelihood L(h) for hypotheses h, the likelihoods from the sub detectors are multiplied as they are assumed to be independent:
L(h) = L^SVD(h) L^CDC(h) L^TOP(h) L^ARICH(h) L^ECL(h) L^KLM(h)
Binary Likelihood(for pion):  R(π/k)=L(π)/(L(k)+L(π))
Global likelihood(for pion):  R(π)=L(π)/(L(k)+L(π)+L(e)+L(u)+L(p)+L(d))
where L(π) is the likelihood of pion, L(k) is the likelihood of kaon, L(e) is the likelihood of electron, L(p) is the likelihood of proton, L(u) is the likelihood of muon, and L(d) is the likelihood of deuteron.
# Hyperparameter used for XGBoost Model training:
1. Objective[binary: logistic]: It defines the loss function to be minimized. Here logistic regression for binary classification is used which outputs the probability. 
2. Learning Rate(0.1): It is the step size at which the optimizer updates the weights. The typical range of the lr is from 0.01 to 0.2. A smaller lr results in slower but accurate updates, while a larger lr results in faster but less accurate updates.
3. Max Depth(10): This is the maximum depth of the tree and is used to control the over-fitting. The typical value for max depth lies between 3 to 10. Above this range, the model is likely to overfit.
4. Subsamples(0.5): It is the fraction of features to be randomly sampled for each tree. The typical value of subsamples is from 0.5 to 1. Below this range, the model is likely to underfit.
# Conclusion
The standard likelihood approach for π/K separation used at Belle II can be improved by using Machine Learning models such as XGBoost that combine the information from different subdetectors using the log-likelihood variables to differentiate between π and K with higher accuracy. 
The success of this approach allows us to extend it to the classification of all six particle species. Also, refinement of the subdetectors in the form of upgraded likelihoods can be easily included by training a new model with these new variables.
