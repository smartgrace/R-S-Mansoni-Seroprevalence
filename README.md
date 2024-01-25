# R-S-Mansoni-Seroprevalence
This is a cluster randomized controlled trial design(RCT). This study is conducted to compare the effect of two mass drug administration strategies: Community-Wide Treatment (CWT) versus School-Based Treatment (SBT) on Schistosoma mansoni seroprevalence. Specifically, we want to investigate the difference in the prevalence of S. mansoni in villages that are either under CWT or SBT over the entire post-treatment period of 2 years.

30 villages were randomized into two study arms - half of them were randomized into CWT arm and the remaining half into SBT arm. In each of the villages, 100 preschool children were aimed to enroll. The data contains information on each village, and it also collects demographic info. for each children, including age, gender, and measures of infection.

There are multiple ways to do the analysis, but note that the independent unit in the trial is the community. Individuals within the same community may have correlations among them. To analyze the data, we can either use an analysis based on community-level means (GEE) or an analysis based on child-level outcomes that account for outcome correlation within the community (linear mixed-effects model).

In this project, I conducted three models to display the process of model building. First, I fitted a linear mixed-effects model to examine the individual level outcomes with random effects for the community, to account for the dependence in the clustered measurement data. The output gives some measures of model fit, and an estimate of the variance explained by the random effect. The random effect here is indistinguishable from 0, the random effect may not matter so we can do a regular linear model instead.

Then I built a general linear regression model, but in the diagnosed plot of residuals against the fitted values, I found that the residuals are not randomly distributed- we can observe a pattern in the distribution, and that means there is some variation in the data that has not been explained. So linear regression model is not a good fit for the data. This can be explained by the presence of clusters - each cluster may have a different variance structure.

Finally, I fitted a General estimating equation model for a marginal analysis based on community-level means. I fitted the models by using different covariance structures, which produces different results, and I selected the most appropriate covariance structure by comparing models’ AIC and BIC. The result of the GEE model differs from that of the general linear regression model, as GEE takes into account the cluster effect while modeling data. The estimated effect of the "arm" variable was 0.04. which means under the same conditions, the prevalence is expected to increase by 0.04 when transitioning from the CWT arm to the SBT arm. However, since the P-value is greater than 0.05, there is no statistically significant difference in the prevalence between the CWT and SBT over the two years, whether the other variables are adjusted or not in the model.
