# Additional Methods
Here we include additional methodological detail on study design and analysis for estimating Infectiousness of SARS-CoV-2 breakthrough infections in vaccinated individuals and reinfections during the Omicron wave using data from California state prisons.

## SARS-CoV-2 testing data
We excluded any false positive or inconclusive test results from the data (0.5% of tests). Often multiple tests were collected from residents on the same day. If multiple SARS-CoV-2 tests were collected from a resident on the same day with conflicting results (0.1% of tests), we excluded all tests from that day if: 1) the type of any test collected was unknown; or 2) the resident received multiple SARS-CoV-2 PCR tests with conflicting results. If a resident received both a SARS-CoV-2 antigen test and a SARS-CoV-2 PCR test on the same day with conflicting results, we excluded the result from the antigen test.


## Matching
We used the MatchIt package to perform 1:10 matching without replacement of unvaccinated index cases to vaccinated cases (*1*). We first estimated propensity scores for index case’s probability of being vaccinated, based on their age, prior SARS-CoV-2 infection history, and COVID-19 risk score using logistic regression. COVID-19 weighted risk score was generated by California Correctional Health Care Services (CCHCS) and reflects literature understanding of comorbidities most associated with severe COVID-19 complications upon infection (*2*). 

We created two distance matrices that reflect pairwise differences between index cases in: 1) propensity scores (caliper = 0.1); and 2) days from first positive test (caliper = 30). We scaled the distance matrix for difference in days to have the same range as the distance matrix for propensity scores and averaged the two distance matrices for matching. The weighting of propensity score versus days from first positive test was varied in sensitivity analysis. Index cases were also matched exactly by institution. Each observation was weighted based on the number of matches.


## Sensitivity analyses
We outline additional detail on some sensitivity analyses conducted to assess robustness of study findings. 

#### Alternative COVID-19 vaccination status in close contacts
In the primary analysis, we controlled for vaccination status in close contacts in terms of number of vaccine doses received 14 days prior to first exposure to index case. We also conducted the regression analysis when treating the close contact’s COVID-19 vaccination status as a binary variable representing any prior vaccination and when combining prior vaccination and prior SARS-CoV-2 infection.

#### Alternative matching for vaccine doses in index cases
For the main analysis examining the relationship between number of vaccine doses and infectiousness of index cases, we reweighted matches between unvaccinated and vaccinated index cases in three groups based on number of vaccine doses (1 dose, 2 doses, 3+ doses). To address concerns on covariate imbalance across the three vaccinated groups, we conducted a separate analysis where we matched the three vaccinated groups separately to a single reference group (unvaccinated group). All other matching specifications remained the same.

#### Time since most recent vaccination or natural infection 
We estimated the unadjusted attack rate of infection among vaccinated index cases, stratified by time since most recent COVID-19 vaccination. We performed three additional regression analyses to evaluate whether time since last vaccine, time since last infection, or time since last vaccine or infection had a relationship with the infectiousness of a SARS-CoV-2 infection. In these analyses, the coefficient of interest was the index case’s time since most recent vaccination or natural infection. The remainder of the analyses remained the same, controlling for all pre-specified covariates in the main analysis.

#### Sensitivity to exclusion criteria
We conducted two sensitivity analyses that relaxed exclusion criteria for index cases and close contacts. In the first analysis, we included close contacts that tested positive within the first 2 days of exposure to an index case. In the second analysis, we removed the requirement that close contacts have a negative test within 2 days of first exposure to an index case. All other aspects of study design remained the same (Table S8).

#### Alternative matching
We repeated the primary analysis with sensitivity analyses on the matching process. We varied the ratio of matches (1:4 matching instead of 1:10) and the calipers of both propensity scores (caliper = 0.05 and caliper = 0.2, instead of 0.1) and time (caliper = 15 days, instead of 30). We tested the sensitivity of matches and study outcomes to the balance between propensity scores and time in the distance matrix; we formulated the distance matrix as a weighted average of differences in propensity scores and time (in 1:3 and 3:1 ratios). We evaluated study outcomes when including race and sex in the propensity score and when not including a propensity score (matching only on time and institution). We additionally repeated the analysis without matching, estimating robust errors instead of cluster-robust errors in the Poisson regression model.

#### Alternative infectious period
We tested the impact of varying assumptions about the start and duration of the infectious period on study outcomes, maintaining all other inclusion and exclusion criteria of the study. In this sensitivity analysis, we assumed the infectious period began on the day of an index case’s positive test and had a duration of 7 days. We included index cases that received a negative PCR test in the last two days of their infectious period and shortened the infectious period accordingly. In another version of this sensitivity analysis, we also varied the start of the infectious period; we assumed the infectious period began 2 days prior to an index case’s first positive test and had a duration of 1) 5 days and 2) 7 days (Table S10). In both of these sensitivity analyses, we additionally excluded index cases that had a negative test in the 2 days prior to their first positive test.

#### Ad26.COV2 vaccine
In the main analysis, we did not explicitly account for vaccine type. However, since Ad26.COV2 has lower vaccine effectiveness than mRNA vaccines available in the incarcerated population, we conducted a sensitivity analysis where we excluded index cases that received the Ad26.COV2 vaccine. We removed index cases that received the Ad26.COV2 vaccine then followed the matching and regression procedures of the primary analysis.

#### Alternative regression model
We used Poisson regression in the main analysis since coefficients are easier to interpret than those in logistic regression and may be more robust with model misspecification (*3*). As a sensitivity analysis, we performed the primary analysis using a logistic regression model instead of a robust Poisson model, incorporating weights from matching as well as cluster-robust standard errors based on matching group membership. We report the odds ratios of infection given prior vaccination or prior infection and 95% confidence intervals.


## References
1. MatchIt: Getting Started. Accessed June 9, 2022. https://cran.r-project.org/web/packages/MatchIt/vignettes/MatchIt.html

2. Covid weighted risk scoring. Main. Published April 13, 2021. Accessed April 27, 2022. https://cdcrdata.miraheze.org/wiki/Supplemental/Covid_weighted_risk_scoring

3. Zou G. A Modified Poisson Regression Approach to Prospective Studies with Binary Data. Am J Epidemiol. 2004;159(7):702-706. doi:10.1093/aje/kwh090
