
<!-- README.md is generated from README.Rmd. Please edit that file -->

# dmpkg

## Installation

First, download the zip file of the package source called
`dmpkg_0.0.0.9007.tar.gz` from [this
link](https://zenodo.org/record/4287448). Then run the code below and
select the zip file you downloaded.

``` r
install.packages(file.choose(), repos = NULL, type="source")
```

## Examples for Plot-based Datamations

``` r
library(dmpkg)
library(animation)
library(tidyverse)

# The command below takes 90 seconds to execute on my machine
saveGIF({
  small_salary %>%
    animate_group_by_sanddance(Degree, nframes = 30) %>%
    animate_summarize_mean_sanddance(Salary, nframes = 30)
}, movie.name="Degree_two_colors.gif", interval = 0.1, ani.width = 500, ani.height = 350, ani.res = 100)

# The command below takes 100 seconds to execute on my machine
saveGIF({
  small_salary %>%
    animate_group_by_sanddance(Degree, Work, nframes = 30) %>%
    animate_summarize_mean_sanddance(Salary, nframes = 30)
}, movie.name="Work_Degree_two_colors.gif", interval = 0.1, ani.width = 500, ani.height = 350, ani.res= 100)
```

## Examples for Table-based Datamations

``` r
library(dmpkg)
library(tidyverse)

# The command below takes 20 seconds to execute on my machine
pipeline <- "small_salary_data %>% group_by(Degree)"
dmpkg::datamation_tibble(pipeline, output = "salary_group_degree.gif")

# The command below takes 40 seconds to execute on my machine
pipeline <- "mtcars %>% group_by(cyl)"
dmpkg::datamation_tibble(pipeline, output = "mtcars_group_cyl.gif")

# The command below takes 50 seconds to execute on my machine
pipeline <- "small_salary_data %>% group_by(Degree, Work) %>% summarize(Avg_Salary = mean(Salary))"
dmpkg::datamation_tibble(pipeline, output = "salary_group2_summarize_mean.gif")
```
