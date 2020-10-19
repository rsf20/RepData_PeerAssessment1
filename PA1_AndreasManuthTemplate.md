---
title: "Reproducible Research: Peer Assessment 1"
author: "Andreas Manuth"
output: 
  html_document:
    keep_md: true
---


## Loading and preprocessing the data
After unzipping the activity data, looking into the csv with a text editor shows this syntax:  
***
"steps","date","interval"  
NA,"2012-10-01",0  
***
For loading data like that *read_csv()* in the *readr* package is perfect, which is here loaded as part of the *tidyverse* library.

```r
library(tidyverse)
```

```
## Warning: package 'tidyverse' was built under R version 3.6.2
```

```
## -- Attaching packages --------------------------------------------------------------------- tidyverse 1.3.0 --
```

```
## v ggplot2 3.2.1     v purrr   0.3.3
## v tibble  2.1.3     v dplyr   0.8.3
## v tidyr   1.0.0     v stringr 1.4.0
## v readr   1.3.1     v forcats 0.4.0
```

```
## Warning: package 'tidyr' was built under R version 3.6.2
```

```
## Warning: package 'readr' was built under R version 3.6.2
```

```
## Warning: package 'forcats' was built under R version 3.6.2
```

```
## -- Conflicts ------------------------------------------------------------------------ tidyverse_conflicts() --
## x dplyr::filter() masks stats::filter()
## x dplyr::lag()    masks stats::lag()
```

```r
activity <- read_csv("activity.csv")
```

```
## Parsed with column specification:
## cols(
##   steps = col_double(),
##   date = col_date(format = ""),
##   interval = col_double()
## )
```
Let's see how much data we got and an first assessment of the values:

```r
dim(activity)
```

```
## [1] 17568     3
```

```r
summary(activity)
```

```
##      steps             date               interval     
##  Min.   :  0.00   Min.   :2012-10-01   Min.   :   0.0  
##  1st Qu.:  0.00   1st Qu.:2012-10-16   1st Qu.: 588.8  
##  Median :  0.00   Median :2012-10-31   Median :1177.5  
##  Mean   : 37.38   Mean   :2012-10-31   Mean   :1177.5  
##  3rd Qu.: 12.00   3rd Qu.:2012-11-15   3rd Qu.:1766.2  
##  Max.   :806.00   Max.   :2012-11-30   Max.   :2355.0  
##  NA's   :2304
```

So 13.1147541% **steps** values are missing. As the median is 0, we can expect most of the entries being zero, i.e. the person not moving more than half of the time reported.


## What is mean total number of steps taken per day?


```r
daily_activity <- group_by(activity, date)
daily_steps_totals <- summarize(daily_activity, day_steps = sum(steps))
daily_steps_mean <- mean(daily_steps_totals$day_steps, rm.na = TRUE)
```
The mean total number of steps taken per day is NA.


## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
