
# The Chi-square (Χ<sup>2</sup>) Test

    When our data includes two categorical variables, we can determine
if there is a statistically significant relationship (or alternatively
dependence) between them with the Chi-square (Χ<sup>2</sup>) test. WIth
the Χ<sup>2</sup> test, we compare the observed counts (our data) with
the expected counts if the data came from the same distributions.

    For this tutorial we will use data from an example offered in [STAT
500 Applied Statistics](https://online.stat.psu.edu/stat500/lesson/8)
where participants were asked to give their party affiliation
(*Democrat* or *Republican*) and their opinion on a tax reform bill
(*Favor*, *Indifferent*, *Opposed*).

|            | Favor | Indifferent | Opposed |
|:-----------|:-----:|:-----------:|:-------:|
| Democrat   |  138  |     83      |   64    |
| Republican |  64   |     67      |   84    |

    The researcher wants to know whether a relationship exists between
party affiliation and opinion so will test the following hypotheses:

<center>
<i>H<sub>0</sub></i>: No relationship exists between party affiliation
and opinion on the tax reform bill
</center>
<center>
<i>H<sub>A</sub></i>: There is a significant relationship between party
affiliation and opinion on the tax reform bill
</center>

### Enter the data

    There are many ways to enter data into R and mostly centers around
preference. Two common ways to enter data into base R are the `matrix()`
and `data.frame()` functions. Note that while they will produce the same
table, they are of different data structures which can be important.
However, either will work here.

### Data types

#### Matrix

``` r
opinion <- matrix(data = c(138, 64, 83, 67, 64, 84),
                  nrow = 2, ncol = 3,
                  dimnames = list(c("Democrat", "Republican"),
                                  c("Favor", "Indifferent", "Oppose")))
```

#### data.frame()

``` r
opinion <- data.frame(Favor = c(138, 64),
                      Indifferent = c(83, 67),
                      Opposed = c(64, 84),
                      row.names = c("Democrat", "Republican"))
```

### Run the Chi-square test

    To run the Chi-square test we simply use the `chisq.test()` function
on our dataset, either as a data frame or matrix.

``` r
chisq.test(opinion)
```

    ## 
    ##  Pearson's Chi-squared test
    ## 
    ## data:  opinion
    ## X-squared = 22.152, df = 2, p-value = 1.548e-05

    The output of the `chisq.test()` function gives us the test
statistic (`X-squared = 22.152`), the degrees of freedom (`df = 2`), and
the p-value associated with the test statistics (`p-value = 1.548e-05`).
Importantly for answering our original question, the p-value is much
less than 0 so that we can conclude that an association does exist
between party affiliation and a person’s opinion on the tax reform bill.

<table>
<tr>
<th>
Observed
</th>
<th>
Expected
</th>
</tr>
<tr>
<td>

|            | Favor | Indifferent | Opposed | Total |
|:-----------|:-----:|:-----------:|:-------:|:-----:|
| Democrat   |  138  |     83      |   64    |  285  |
| Republican |  64   |     67      |   84    |  215  |
| Total      |  202  |     150     |   148   |  500  |

</td>
<td>

|            | Favor  | Indifferent | Opposed |
|:-----------|:------:|:-----------:|:-------:|
| Democrat   | 115.14 |    85.5     |  84.36  |
| Republican | 86.86  |    64.5     |  63.64  |

</td>
</tr>
</table>
<!-- Tab links -->

<div class="tab">

<button class="tablinks" onclick="openCity(event, 'London')">London</button>
<button class="tablinks" onclick="openCity(event, 'Paris')">Paris</button>
<button class="tablinks" onclick="openCity(event, 'Tokyo')">Tokyo</button>

</div>

<!-- Tab content -->

<div id="London" class="tabcontent">

<h3>
London
</h3>
<p>
London is the capital city of England.
</p>

</div>

<div id="Paris" class="tabcontent">

<h3>
Paris
</h3>
<p>
Paris is the capital of France.
</p>

</div>

<div id="Tokyo" class="tabcontent">

<h3>
Tokyo
</h3>
<p>
Tokyo is the capital of Japan.
</p>

</div>