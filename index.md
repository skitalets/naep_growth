---
title       : Visualizing Student Achievement
subtitle    : An Exploration of the National Assessment of Educational Progress
author      : Chris Tessone
job         : Student, JHU Data Science Specialization
logo        : bloomberg_shield.png
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [bootstrap, quiz]
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## NAEP: The Nation's Report Card

The National Assessment of Educational Progress (NAEP) measures student
achievement across the United States using standardized tests in a variety of
subjects. NAEP is not a test of *individual* or even school-level achievement;
it measures how students throughout the country are achieving, with breakouts
for some tests by state, race, gender, and socioeconomic status.

As you'll see in this presentation, the [NAEP Visualizer](http://skitalets.shinyapps.io/naep/)
allows users to build animations of growth on this important standardized
test easily, slicing the data based on gender and grade level.

---

## How NAEP Differs from "High-Stakes" State Tests

Some key features of NAEP that distinguish it from some other standardized
tests that are widely discussed in K-12 education, especially so-called
"high stakes" state tests:

- NAEP is a *sample*. Not all students are tested.
- NAEP can be used to directly compare states. Unlike the annual tests mandated
by No Child Left Behind, the same tests are used from state to state. However,
the state results include only public school students, not those in private
schools.
- NAEP provides only limited ability to compare U.S. students to their
counterparts in other countries, via the NAEP-TIMSS Linking Study. It is most
useful for comparisons within the United States.

--- .class #id 

## Scores Grew Modestly 2003-2013



The [NAEP Visualizer](http://skitalets.shinyapps.io/naep/) allows users to
see growth in scores on NAEP's math and reading from 2003-2013. During that
ten-year period, scores grew modestly, increasing on average 2.61
percent in math and 1.51 percent in reading.


```r
dc.growth.8 <- round((naep[year == 2013 & gender == "all" & grade == 8 &
                            state == "District of Columbia", scale.score.math] /
        naep[year == 2003 & gender == "all" & grade == 8 &
                     state == "District of Columbia", scale.score.math]
        - 1) * 100, 2)
```

The average growth masks interesting variability among states that is worth
exploring. For example, the complex code above calculates that the District of
Columbia's public school students improved by 9.13 percent in math
during the same period. The visualizer helps see how individual states move when
you click on that state's bubble before pressing play and enables much easier
slicing and dicing of the data.

--- &radio

## Test Your NAEP Knowledge

NAEP allows users to make useful comparisons of achievement between which
groups on multiple subjects and grade-levels (choose the best answer).

1. American and Finnish girls.
2. Utahn and Bay Stater boys in private schools.
3. _Virginian and Hawaiian girls in public schools._
4. Boys and girls of German origin in public schools across the United States.

*** .hint
NAEP measures very specific types of achievement. Not all subgroups are included
in the NAEP tests.

*** .explanation
The correct answer is Virginian and Hawaiian girls in public schools. NAEP
provides data only on public school students in the state results. National
origin is not one of NAEP's subgroups. While limited international comparisons
are possible via the NAEP-TIMSS Linking Study, only a small number of
grade/subject/year combinations is available.
