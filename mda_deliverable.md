
# Mini Data-Analysis Deliverable 1

# Welcome to your (maybe) first-ever data analysis project!

And hopefully the first of many. Let’s get started:

1.  Install the [`datateachr`](https://github.com/UBC-MDS/datateachr)
    package by typing the following into your **R terminal**:

<!-- -->

    install.packages("devtools")
    devtools::install_github("UBC-MDS/datateachr")

2.  Load the packages below.

``` r
library(datateachr) 
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.3     ✔ readr     2.1.4
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.0
    ## ✔ ggplot2   3.4.3     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.2     ✔ tidyr     1.3.0
    ## ✔ purrr     1.0.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

3.  Make a repository in the <https://github.com/stat545ubc-2023>
    Organization. You can do this by following the steps found on canvas
    in the entry called [MDA: Create a
    repository](https://canvas.ubc.ca/courses/126199/pages/mda-create-a-repository).
    One completed, your repository should automatically be listed as
    part of the stat545ubc-2023 Organization.

# Instructions

## For Both Milestones

- Each milestone has explicit tasks. Tasks that are more challenging
  will often be allocated more points.

- Each milestone will be also graded for reproducibility, cleanliness,
  and coherence of the overall Github submission.

- While the two milestones will be submitted as independent
  deliverables, the analysis itself is a continuum - think of it as two
  chapters to a story. Each chapter, or in this case, portion of your
  analysis, should be easily followed through by someone unfamiliar with
  the content.
  [Here](https://swcarpentry.github.io/r-novice-inflammation/06-best-practices-R/)
  is a good resource for what constitutes “good code”. Learning good
  coding practices early in your career will save you hassle later on!

- The milestones will be equally weighted.

## For Milestone 1

**To complete this milestone**, edit [this very `.Rmd`
file](https://raw.githubusercontent.com/UBC-STAT/stat545.stat.ubc.ca/master/content/mini-project/mini-project-1.Rmd)
directly. Fill in the sections that are tagged with
`<!--- start your work below --->`.

**To submit this milestone**, make sure to knit this `.Rmd` file to an
`.md` file by changing the YAML output settings from
`output: html_document` to `output: github_document`. Commit and push
all of your work to the mini-analysis GitHub repository you made
earlier, and tag a release on GitHub. Then, submit a link to your tagged
release on canvas.

**Points**: This milestone is worth 36 points: 30 for your analysis, and
6 for overall reproducibility, cleanliness, and coherence of the Github
submission.

# Learning Objectives

By the end of this milestone, you should:

- Become familiar with your dataset of choosing
- Select 4 questions that you would like to answer with your data
- Generate a reproducible and clear report using R Markdown
- Become familiar with manipulating and summarizing your data in tibbles
  using `dplyr`, with a research question in mind.

# Task 1: Choose your favorite dataset

The `datateachr` package by Hayley Boyce and Jordan Bourak currently
composed of 7 semi-tidy datasets for educational purposes. Here is a
brief description of each dataset:

- *apt_buildings*: Acquired courtesy of The City of Toronto’s Open Data
  Portal. It currently has 3455 rows and 37 columns.

- *building_permits*: Acquired courtesy of The City of Vancouver’s Open
  Data Portal. It currently has 20680 rows and 14 columns.

- *cancer_sample*: Acquired courtesy of UCI Machine Learning Repository.
  It currently has 569 rows and 32 columns.

- *flow_sample*: Acquired courtesy of The Government of Canada’s
  Historical Hydrometric Database. It currently has 218 rows and 7
  columns.

- *parking_meters*: Acquired courtesy of The City of Vancouver’s Open
  Data Portal. It currently has 10032 rows and 22 columns.

- *steam_games*: Acquired courtesy of Kaggle. It currently has 40833
  rows and 21 columns.

- *vancouver_trees*: Acquired courtesy of The City of Vancouver’s Open
  Data Portal. It currently has 146611 rows and 20 columns.

**Things to keep in mind**

- We hope that this project will serve as practice for carrying our your
  own *independent* data analysis. Remember to comment your code, be
  explicit about what you are doing, and write notes in this markdown
  document when you feel that context is required. As you advance in the
  project, prompts and hints to do this will be diminished - it’ll be up
  to you!

- Before choosing a dataset, you should always keep in mind **your
  goal**, or in other ways, *what you wish to achieve with this data*.
  This mini data-analysis project focuses on *data wrangling*,
  *tidying*, and *visualization*. In short, it’s a way for you to get
  your feet wet with exploring data on your own.

And that is exactly the first thing that you will do!

1.1 **(1 point)** Out of the 7 datasets available in the `datateachr`
package, choose **4** that appeal to you based on their description.
Write your choices below:

**Note**: We encourage you to use the ones in the `datateachr` package,
but if you have a dataset that you’d really like to use, you can include
it here. But, please check with a member of the teaching team to see
whether the dataset is of appropriate complexity. Also, include a
**brief** description of the dataset here to help the teaching team
understand your data.

<!-------------------------- Start your work below ---------------------------->

**1: vancouver_trees  
2: parking_meters  
3: flow_sample  
4: steam_games**

<!----------------------------------------------------------------------------->

1.2 **(6 points)** One way to narrowing down your selection is to
*explore* the datasets. Use your knowledge of dplyr to find out at least
*3* attributes about each of these datasets (an attribute is something
such as number of rows, variables, class type…). The goal here is to
have an idea of *what the data looks like*.

*Hint:* This is one of those times when you should think about the
cleanliness of your analysis. I added a single code chunk for you below,
but do you want to use more than one? Would you like to write more
comments outside of the code chunk?

<!-------------------------- Start your work below ---------------------------->

    # Attribute 1: Using glimpse() to get the dimensions of the table, the class of variables, and sample of top rows.
    glimpse(vancouver_trees)
    glimpse(parking_meters)
    glimpse(flow_sample)
    glimpse(steam_games)

    # Attribute 2: Using top_n() to sample first 10 rows of table for particular variable of interest.
    top_n(vancouver_trees, 10, common_name)
    top_n(parking_meters, 10, geo_local_area)
    top_n(flow_sample, 10, flow)
    top_n(steam_games, 10, developer)

    # Attribute 3: Using count() and/or arrange(desc()) to determine how many samples in leading categories for a particular variable of interest.
    vancouver_trees %>% 
      count(genus_name) %>% 
      arrange(desc(n))  

    parking_meters %>% 
      count(geo_local_area) %>% 
      arrange(desc(n))  

    flow_sample %>% 
      arrange(desc(flow))  

    steam_games %>% 
      count(developer) %>% 
      arrange(desc(n))

<!----------------------------------------------------------------------------->

1.3 **(1 point)** Now that you’ve explored the 4 datasets that you were
initially most interested in, let’s narrow it down to 1. What lead you
to choose this one? Briefly explain your choice below.

<!-------------------------- Start your work below ---------------------------->

**I will be selecting the vancouver_trees dataset. I study forestry and
am most interested intrinsically, and I think there are mulitple
different variables of interest to evaluate the relationships between.**

<!----------------------------------------------------------------------------->

1.4 **(2 points)** Time for a final decision! Going back to the
beginning, it’s important to have an *end goal* in mind. For example, if
I had chosen the `titanic` dataset for my project, I might’ve wanted to
explore the relationship between survival and other variables. Try to
think of 1 research question that you would want to answer with your
dataset. Note it down below.

<!-------------------------- Start your work below ---------------------------->

**My immediate idea is evaluating the relationship between DBH and
species/genus. This is similair to data analysis that might take place
during any forestry survey and it will be interesting to see what kind
of trees are the largest in Vancouver. Dominant species/genus will
likely be my categorical explanatory variable while DBH will be
continuous response variable.**

<!----------------------------------------------------------------------------->

# Important note

Read Tasks 2 and 3 *fully* before starting to complete either of them.
Probably also a good point to grab a coffee to get ready for the fun
part!

This project is semi-guided, but meant to be *independent*. For this
reason, you will complete tasks 2 and 3 below (under the **START HERE**
mark) as if you were writing your own exploratory data analysis report,
and this guidance never existed! Feel free to add a brief introduction
section to your project, format the document with markdown syntax as you
deem appropriate, and structure the analysis as you deem appropriate. If
you feel lost, you can find a sample data analysis
[here](https://www.kaggle.com/headsortails/tidy-titarnic) to have a
better idea. However, bear in mind that it is **just an example** and
you will not be required to have that level of complexity in your
project.

# Task 2: Exploring your dataset

If we rewind and go back to the learning objectives, you’ll see that by
the end of this deliverable, you should have formulated *4* research
questions about your data that you may want to answer during your
project. However, it may be handy to do some more exploration on your
dataset of choice before creating these questions - by looking at the
data, you may get more ideas. **Before you start this task, read all
instructions carefully until you reach START HERE under Task 3**.

2.1 **(12 points)** Complete *4 out of the following 8 exercises* to
dive deeper into your data. All datasets are different and therefore,
not all of these tasks may make sense for your data - which is why you
should only answer *4*.

Make sure that you’re using dplyr and ggplot2 rather than base R for
this task. Outside of this project, you may find that you prefer using
base R functions for certain tasks, and that’s just fine! But part of
this project is for you to practice the tools we learned in class, which
is dplyr and ggplot2.

1.  Plot the distribution of a numeric variable.
2.  Create a new variable based on other variables in your data (only if
    it makes sense)
3.  Investigate how many missing values there are per variable. Can you
    find a way to plot this?
4.  Explore the relationship between 2 variables in a plot.
5.  Filter observations in your data according to your own criteria.
    Think of what you’d like to explore - again, if this was the
    `titanic` dataset, I may want to narrow my search down to passengers
    born in a particular year…
6.  Use a boxplot to look at the frequency of different observations
    within a single variable. You can do this for more than one variable
    if you wish!
7.  Make a new tibble with a subset of your data, with variables and
    observations that you are interested in exploring.
8.  Use a density plot to explore any of your variables (that are
    suitable for this type of plot).

2.2 **(4 points)** For each of the 4 exercises that you complete,
provide a *brief explanation* of why you chose that exercise in relation
to your data (in other words, why does it make sense to do that?), and
sufficient comments for a reader to understand your reasoning and code.

<!-------------------------- Start your work below ---------------------------->

<br>

### Exploring My Dataset

#### 2.1: Exploring the data with 4 exercises

<br>

##### **Data Exploration 1**

Exercise 7: Creating a new tibble to isolate the variable of interest
and make the data more manageable:

``` r
head(vancouver_trees)
```

    ## # A tibble: 6 × 20
    ##   tree_id civic_number std_street genus_name species_name cultivar_name  
    ##     <dbl>        <dbl> <chr>      <chr>      <chr>        <chr>          
    ## 1  149556          494 W 58TH AV  ULMUS      AMERICANA    BRANDON        
    ## 2  149563          450 W 58TH AV  ZELKOVA    SERRATA      <NA>           
    ## 3  149579         4994 WINDSOR ST STYRAX     JAPONICA     <NA>           
    ## 4  149590          858 E 39TH AV  FRAXINUS   AMERICANA    AUTUMN APPLAUSE
    ## 5  149604         5032 WINDSOR ST ACER       CAMPESTRE    <NA>           
    ## 6  149616          585 W 61ST AV  PYRUS      CALLERYANA   CHANTICLEER    
    ## # ℹ 14 more variables: common_name <chr>, assigned <chr>, root_barrier <chr>,
    ## #   plant_area <chr>, on_street_block <dbl>, on_street <chr>,
    ## #   neighbourhood_name <chr>, street_side_name <chr>, height_range_id <dbl>,
    ## #   diameter <dbl>, curb <chr>, date_planted <date>, longitude <dbl>,
    ## #   latitude <dbl>

``` r
trees_tbl <- select(vancouver_trees, genus_name, diameter, neighbourhood_name, common_name, date_planted )
top_n(trees_tbl, 5)
```

    ## Selecting by date_planted

    ## # A tibble: 5 × 5
    ##   genus_name diameter neighbourhood_name common_name              date_planted
    ##   <chr>         <dbl> <chr>              <chr>                    <date>      
    ## 1 STEWARTIA         3 GRANDVIEW-WOODLAND JAPANESE STEWARTIA       2019-06-13  
    ## 2 PARROTIA          3 MOUNT PLEASANT     VANESSA PERSIAN IRONWOOD 2019-07-03  
    ## 3 PRUNUS            3 MARPOLE            KWANZAN FLOWERING CHERRY 2019-06-16  
    ## 4 PRUNUS            3 MARPOLE            KWANZAN FLOWERING CHERRY 2019-06-16  
    ## 5 PRUNUS            3 MARPOLE            KWANZAN FLOWERING CHERRY 2019-06-16

``` r
# Before using as_tibble to convert to a tibble I used class() and found that it was already a tibble. 
class(trees_tbl)  
```

    ## [1] "tbl_df"     "tbl"        "data.frame"

<br>

##### **Data Exploration 2**

Exercise 1: Determining the distribution of the numeric variable
(diameter) to start wrapping my head around the data and considering
what kind of relationships may be present and what analysis might be
required:

``` r
ggplot(trees_tbl, aes(diameter)) +
geom_histogram()
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](mda_deliverable_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

Looks like a left-skewed distribution, but the scale is way too big, so
there may be outliers. Going to investigate max values of diameter using
arrange(desc())to ensure there are no apparent data entry errors.

``` r
arrange(trees_tbl, desc(diameter))
```

    ## # A tibble: 146,611 × 5
    ##    genus_name     diameter neighbourhood_name  common_name          date_planted
    ##    <chr>             <dbl> <chr>               <chr>                <date>      
    ##  1 STYRAX              435 HASTINGS-SUNRISE    JAPANESE SNOWBELL    2003-03-25  
    ##  2 ACER                317 KITSILANO           MAPLE SPECIES        1993-11-01  
    ##  3 QUERCUS             305 DUNBAR-SOUTHLANDS   WILLOW OAK           2000-04-20  
    ##  4 ACER                182 MARPOLE             SILVER MAPLE         NA          
    ##  5 ACER                161 MARPOLE             NORWAY MAPLE         NA          
    ##  6 ACER                156 KERRISDALE          SCHWEDLER NORWAY MA… NA          
    ##  7 ACER                151 DOWNTOWN            RED MAPLE            NA          
    ##  8 ULMUS               144 VICTORIA-FRASERVIEW BRANDON ELM          2000-02-03  
    ##  9 PRUNUS              141 SOUTH CAMBIE        KWANZAN FLOWERING C… NA          
    ## 10 CERCIDIPHYLLUM      131 VICTORIA-FRASERVIEW KATSURA TREE         NA          
    ## # ℹ 146,601 more rows

Wow, there’s a lot of funny business, several trees have diameters over
100 (inches), and the three largest were planted in the last 30 years,
so there is definitely some erroneous data here. We’ll remove the trees
that are greater than 100 inch diameter in in the next step…  
<br>

##### **Data Exploration 3**

Exercise 5: We will use filter() to remove the outliers (greater than
100 inches):

``` r
trees_tbl <- filter(trees_tbl, diameter < 100 )

#And now our largest diameters are 99:
arrange(trees_tbl, desc(diameter))
```

    ## # A tibble: 146,601 × 5
    ##    genus_name    diameter neighbourhood_name       common_name      date_planted
    ##    <chr>            <dbl> <chr>                    <chr>            <date>      
    ##  1 CORNUS              99 SHAUGHNESSY              PACIFIC DOGWOOD  NA          
    ##  2 CHAMAECYPARIS       99 SHAUGHNESSY              LAWSON CYPRESS/… NA          
    ##  3 SORBUS              99 KENSINGTON-CEDAR COTTAGE EUROPEAN MOUNTA… NA          
    ##  4 CASTANEA            99 SHAUGHNESSY              AMERICAN CHESTN… NA          
    ##  5 CORNUS              99 SHAUGHNESSY              PACIFIC DOGWOOD  NA          
    ##  6 CORNUS              99 SHAUGHNESSY              PACIFIC DOGWOOD  NA          
    ##  7 CORNUS              99 SHAUGHNESSY              PACIFIC DOGWOOD  NA          
    ##  8 CORNUS              99 SHAUGHNESSY              PACIFIC DOGWOOD  NA          
    ##  9 TILIA               99 RENFREW-COLLINGWOOD      DEGROOT LINDEN   1996-04-15  
    ## 10 QUERCUS             99 FAIRVIEW                 PIN OAK          NA          
    ## # ℹ 146,591 more rows

<br>

##### **Data Exploration 4**

Exercise 4: Assess the relationship between two variables. We’ll look at
diameter and neighborhood:

``` r
ggplot(trees_tbl, aes(x = neighbourhood_name, y = diameter))+
  geom_boxplot(alpha = .5, aes(color = neighbourhood_name))+ 
  scale_x_discrete(label = function(x) stringr::str_trunc(x, 9))+
  theme(axis.text.x = element_text(angle = 90), legend.position = "none")+
  labs(x = "Neighborhood", y = "Diameter", title = "Diameter by Neighborhood")
```

![](mda_deliverable_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

Upon first glance, average DBH appears to be quite similar among the
different neighborhoods, thought there is some clear variation (downtown
has notably smaller trees).

<br>

#### 2.2: Justifying exercise decisions

<br>

**1)** I chose exercise 7 to create a smaller tibble than the original
vancouver_trees tibble because there were several columns making it
difficult to visualize the data. I selected the five variables that I am
most interested in comparing the relationships between.

**2)** Next, I followed exercise 1 to plot the distribution of the
continuous variable, diameter. The histogram helped to visualize the
general tendency of the data which is left skewed, and made the outliers
apparent.

**3)** After recognizing the presence of outliers, I decided to use
exercise 5 to filter rows by diameters grater than 100 and remove
outliers. Trees can certainly get larger than 100 inches here in
Vancouver, but many of the trees larger than 100 inches had planting
dates within the last 30 years, so given the limited infomration I have
on data collection and the abundance of outliers I just set a cutoff of
100 DBH so as to move on with analysis.

**4)** Last, I followed exercise 4 to begin assessing the relationships
between variables. I created a boxplot comparing tree diameters by
neighborhood. This plot helps to visualize data and make plans for
further analysis. Mean DBH appears similar across neighborhoods but
there are definite deviations to explore.

<br>

<!----------------------------------------------------------------------------->

# Task 3: Choose research questions

**(4 points)** So far, you have chosen a dataset and gotten familiar
with it through exploring the data. You have also brainstormed one
research question that interested you (Task 1.4). Now it’s time to pick
4 research questions that you would like to explore in Milestone 2!
Write the 4 questions and any additional comments below.

<!--- *****START HERE***** --->

**4 Potential Research Questions:**

**1)** How does average tree diameter vary by neighborhood?

**2)** How does average tree diameter vary species?

**3)** How does tree species distribution vary by neighborhood?

**4)** Which species is the fastest growing? (determine plant age from
plant date and compare across species)

<!----------------------------->

# Overall reproducibility/Cleanliness/Coherence Checklist

## Coherence (0.5 points)

The document should read sensibly from top to bottom, with no major
continuity errors. An example of a major continuity error is having a
data set listed for Task 3 that is not part of one of the data sets
listed in Task 1.

## Error-free code (3 points)

For full marks, all code in the document should run without error. 1
point deduction if most code runs without error, and 2 points deduction
if more than 50% of the code throws an error.

## Main README (1 point)

There should be a file named `README.md` at the top level of your
repository. Its contents should automatically appear when you visit the
repository on GitHub.

Minimum contents of the README file:

- In a sentence or two, explains what this repository is, so that
  future-you or someone else stumbling on your repository can be
  oriented to the repository.
- In a sentence or two (or more??), briefly explains how to engage with
  the repository. You can assume the person reading knows the material
  from STAT 545A. Basically, if a visitor to your repository wants to
  explore your project, what should they know?

Once you get in the habit of making README files, and seeing more README
files in other projects, you’ll wonder how you ever got by without them!
They are tremendously helpful.

## Output (1 point)

All output is readable, recent and relevant:

- All Rmd files have been `knit`ted to their output md files.
- All knitted md files are viewable without errors on Github. Examples
  of errors: Missing plots, “Sorry about that, but we can’t show files
  that are this big right now” messages, error messages from broken R
  code
- All of these output files are up-to-date – that is, they haven’t
  fallen behind after the source (Rmd) files have been updated.
- There should be no relic output files. For example, if you were
  knitting an Rmd to html, but then changed the output to be only a
  markdown file, then the html file is a relic and should be deleted.

(0.5 point deduction if any of the above criteria are not met. 1 point
deduction if most or all of the above criteria are not met.)

Our recommendation: right before submission, delete all output files,
and re-knit each milestone’s Rmd file, so that everything is up to date
and relevant. Then, after your final commit and push to Github, CHECK on
Github to make sure that everything looks the way you intended!

## Tagged release (0.5 points)

You’ve tagged a release for Milestone 1.

### Attribution

Thanks to Icíar Fernández Boyano for mostly putting this together, and
Vincenzo Coia for launching.
