library(tidyverse)
#install.packages("ggplot2")#
#library(ggplot2)#
DailyActivity <-read.csv("C:/Users/King/Documents/Google Data Cert/Fitabase Data 4.12.16-5.12.16/dailyActivity_merged.csv")
head(DailyActivity)
SleepDay <-read.csv("C:/Users/King/Documents/Google Data Cert/Fitabase Data 4.12.16-5.12.16/sleepDay_merged.csv")
head(SleepDay)
Weightlog_info <-read.csv("C:/Users/King/Documents/Google Data Cert/Fitabase Data 4.12.16-5.12.16/weightLoginfo_merged.csv")
head(Weightlog_info)
view(DailyActivity)
view(SleepDay)
view(Weightlog_info)
print(ncol(DailyActivity))
print(nrow(DailyActivity))
print(colnames(DailyActivity))

print(ncol(SleepDay))
print(nrow(SleepDay))
print(colnames(SleepDay))

print(ncol(Weightlog_info))
print(nrow(Weightlog_info))
print(colnames(Weightlog_info))

#How many unique participants are in each data frame?#
n_distinct(DailyActivity$Id)             #Answer: 33#
n_distinct(SleepDay$Id)                  #Answer: 24#
n_distinct(Weightlog_info$Id)            #Answer: 8#

#Displaying summaries of the following datasets #

DailyActivity %>%
  select(TotalSteps, TotalDistance, VeryActiveDistance,	ModeratelyActiveDistance,	LightActiveDistance, SedentaryMinutes, VeryActiveMinutes, FairlyActiveMinutes, LightlyActiveMinutes) %>%
  summary()

SleepDay %>%
  select(TotalMinutesAsleep, TotalTimeInBed) %>%
  summary()

Weightlog_info %>%
  select(WeightKg, WeightPounds,Fat, BMI) %>%
  summary()

#Visualizing the data
#Calories burnt vs. total steps

ggplot(DailyActivity, aes(x=TotalSteps, y=Calories)) + 
  geom_point()+ geom_smooth() + labs(title="Calories Burnt vs. Total steps")

ggplot(SleepDay, aes(x=TotalMinutesAsleep, y=TotalTimeInBed)) + 
  geom_point()+ geom_smooth() + labs(title="Total Minutes A Sleep vs. Total Time in Bed")


