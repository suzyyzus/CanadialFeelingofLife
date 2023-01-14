# What Factors Affect Feelings of Life of Canadian :tent::tent:

Nowadays, increased people start to think about how to make their lives happier, some people would suggest that making more money would make their lives better, while some people think that spending less time on working would make their lives more enjoyable, but there is no common correct answer to this question. In this report, we are interested in what factors would affect the feelings of life, how would things such as working hours, education, and income, making feelings of life different. We obtained a dataset of the general social survey in 2017, including the information of over 20000 subjects with information categories like feelings of life, education, mental health, etc. We use this dataset and built a linear regression model, found that education, self-rate mental health, income, and the number of marriages all have a positive or negative impact on feelings of life, and people, by using this model, would be able to figure out how to improve their feelings of life.

Highlight of my code

```{r, include=FALSE}
gss_data$education<-as.factor(gss_data$education)
gss_data$average_hours_worked<-as.factor(gss_data$average_hours_worked)
gss_data$self_rated_mental_health<-as.factor(gss_data$self_rated_mental_health)
gss_data$income_respondent<-as.factor(gss_data$income_respondent)
gss_data$education <- factor(gss_data$education, ordered = FALSE)
gss_data$average_hours_worked <- factor(gss_data$average_hours_worked, ordered = FALSE)
gss_data$self_rated_mental_health <- factor(gss_data$self_rated_mental_health, ordered = FALSE)
gss_data$income_respondent <- factor(gss_data$income_respondent, ordered = FALSE)
```

```{r, include=FALSE}
N=30633177
n=length(gss_data$feelings_life)
srs = rep(N, n)
srs_data <- svydesign(id=~1, data=gss_data, fpc=srs)
svy_srs <- svyglm(feelings_life ~ education+average_hours_worked+
                    self_rated_mental_health+income_respondent+number_marriages
                  , srs_data, family="gaussian")
```


```{r, include=FALSE}
summary.lm(svy_srs)
```
