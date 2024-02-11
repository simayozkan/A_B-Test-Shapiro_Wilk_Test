import itertools
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
# !pip install statsmodels
import statsmodels.stats.api as sms
from scipy.stats import ttest_1samp, shapiro, levene, ttest_ind, mannwhitneyu, \
    pearsonr, spearmanr, kendalltau, f_oneway, kruskal
from statsmodels.stats.proportion import proportions_ztest

pd.set_option('display.max_columns', None)
pd.set_option('display.max_rows', 10)
pd.set_option('display.float_format', lambda x: '%.5f' % x)

df = pd.read_csv("/Users/simayozkan/Desktop/ds/AB_Test_Results.csv")

df.head()

df.info()

df.isna().sum()

df.describe().T

#h0 : no statistically difference between variant name and revenue
#h1 : statistically difference between variant name and revenue

test_stat, pvalue = shapiro(df.loc[df["VARIANT_NAME"] == "control", "REVENUE"])
print('Test Stat = %.4f, p-value = %.4f' % (test_stat, pvalue))

#Reject null hypothesis. p-value is lower than 0.05

test_stat, pvalue = shapiro(df.loc[df["VARIANT_NAME"] == "variant", "REVENUE"])
print('Test Stat = %.4f, p-value = %.4f' % (test_stat, pvalue))

#Reject null hypothesis. p-value is lower than 0.05. Normality assumption doesn't hold so we need to use nonparametric test.

test_stat, pvalue = mannwhitneyu(df.loc[df["VARIANT_NAME"] == "control", "REVENUE"],
                                 df.loc[df["VARIANT_NAME"] == "variant", "REVENUE"])

print('Test Stat = %.4f, p-value = %.4f' % (test_stat, pvalue))

#P-value is larger than 0.05 so there is no statistically difference between variant name and revenue
