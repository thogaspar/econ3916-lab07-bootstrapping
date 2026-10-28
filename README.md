# econ3916-lab07-bootstrapping
Econ 3916 Lab 07 - Estimation &amp; Bootstrapping
# Estimation & Bootstrapping — Quantifying Uncertainty Without a Formula

## Objective

I used the UCI Adult Census Income data and simulation to compare formula-based and bootstrap methods for measuring the uncertainty of an estimate.

## Methodology

- Loaded the UCI Adult Census Income data (32,561 respondents).
- Separated the standard deviation of the data from the standard error of an estimate, and checked the s/sqrt(n) relationship across four sample sizes.
- Built parametric confidence intervals from the CLT, and compared how quickly the CLT converges for age and for capital gains.
- Ran the bootstrap by hand, then with `scipy.stats.bootstrap`.
- Examined the bootstrap standard error of the median of the 32,561 whole-number ages.
- Compared percentile and BCa intervals on a heavily skewed variable.
- Bootstrapped a two-sample difference in mean weekly hours.
- Asked an AI to write a bootstrap-interval function, revised my prompt once, and checked the function against my own intervals.
- Ran a coverage simulation on lognormal data at n=50, for both the mean and the median.

## Key Findings

- **Spread versus uncertainty:** The standard deviation describes the data, while the standard error describes an estimate. I checked the s/sqrt(n) relationship across four sample sizes.
- **CLT speed:** The CLT converges quickly for age and slowly for capital gains.
- **A degenerate bootstrap case:** The bootstrap standard error of the median of the 32,561 whole-number ages is exactly 0.0000. With that many ties, every resample returns the same median. The bootstrap is reporting a real property of the data, not failing.
- **Coverage for the mean (lognormal, n=50):** The nominal 95% parametric interval covered 92.5% and the percentile bootstrap covered 91.5%. The gap is inside the Monte Carlo standard error of about 1.3 points, so the two methods are indistinguishable here and both under-cover slightly.
- **Coverage for the median (lognormal, n=50):** The mean-centred parametric interval covered only about 66.8%, while the bootstrap held near its nominal level.
- **Takeaway:** For the mean, the bootstrap gave no advantage over the formula. For the median, where no simple formula fits, the bootstrap was far better.
