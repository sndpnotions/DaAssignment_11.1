# DaAssignment_11.1
# 1. Use the given link and locate the bank marketing dataset. Data Set Link
# Perform the below operations:

# a. Create a visual for representing missing values in the dataset.

install.packages("Amelia")
library(Amelia)
missmap(bank)

# As per the Missing map of bank Df Missing rate is 0% so there are no miising values in this data.
# We can verify the same with below command.

isTRUE(is.na(bank))
install.packages("ggplot2")
library(ggplot2)

# b. Show a distribution of clients based on a Job.

ggplot(bank, aes(x=job, y=age, fill=job)) +   
  geom_boxplot(alpha=0.6) +
  ggtitle("Age based on job")

# c. Check whether is there any relation between Job and Marital Status?

# Using chi-square 
# Null hypothesis : Ho: No relation 
# Ha: Relation between job and marital

chisq.test(bank$job ,bank$marital)

# Pearson's Chi-squared test
# data: bank$job and bank$marital
# X-squared = 373.18, df = 22, p-value < 2.2e-16
# As p-value is less than 0.05 we can reject Null hypothesis. 
# There is significant relation between job and marital.

# d. Check whether is there any association between Job and Education?

chisq.test(bank$job ,bank$education)

# Pearson's Chi-squared test
# data:  bank$job and bank$education
# X-squared = 2840, df = 33, p-value < 2.2e-16
# As p-value is less than 0.05 we can reject Null hypothesis. 
# There is significant relation between job and education.
