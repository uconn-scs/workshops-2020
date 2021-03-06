Introduction to R
================

*QUESTION: How many of you have used R before?* <br> R is a powerful
tool for analyzing and visualizing data Specifically, it is a language
and environment for statistical computing and graphics. As an R user you
will need to learn to understand the language R uses to execute
commands. And that is what we will hopefully help you with today.

*QUESTION: How many of you have used RStudio before?* <br> RStudio is an
open source R integrated development environment for interfacing with
R.It is useful for:

  - Writing scripts for specific analyses
  - Creating markdown documents
  - Version control via GitHub
  - Organizing and sharing analyses via projects

### Navigating RStudio

When we first open RStudio we see that the interface is divided into 3
main windows:

  - Console + Terminal
  - Environment + History + Connections
  - Files + Plots + Packages + Help + Viewer

Once we open a file, such as an R script and editor window will also
open on the LHS.

There are two main ways one can work within RStudio.

1.  Test and play within the interactive R console then copy code into a
    `.R` file to run later.

<!-- end list -->

  - This works well when doing small tests and initially starting off.
  - It quickly becomes laborious
  - Harder to keep track of what you’ve done

In the console window you will see a `>` symbol, which is an interactive
command prompt.

  - It operates on the same idea of a “Read, evaluate, print loop”: you
    type in commands, R tries to execute them, and then returns a
    result.
  - This is similar to what you’d see in a terminal or command prompt.

<!-- end list -->

2.  Start writing in an .R file and use RStudio’s short cut keys for the
    Run command to push the current line, selected lines or modified
    lines to the interactive R console.

<!-- end list -->

  - This is a great way to start; all your code is saved for later.
  - Can easily share code this way.

## Working in R

**Using R as a calculator** <br> Let’s start programming by getting R to
do some arithmetic for us. I am going to do this in the editor window. I
have linked this file to dropbox, so that you can access all of the
coding I am doing via the link in the etherpad. There may be a bit of
delay, but I will try to remember to save frequently so that it stays
relatively up to date.

There are a few different ways to run commands or ‘chunks’ of code from
the editor window, depending on the OS you are using:

  - Click run (all systems)
  - Ctrl + Enter (Win, Linux)
  - Cmd + Enter (Mac OS)

NOTES: \* You can run multiple lines of code at once \* You can run
lines without highlighting, code will run on line with cursor

So let’s start by running some code to do some addition:

``` r
53 + 23 # [Ctrl + Enter]
```

Remember to actually run this we hit ctrl or cmd + enter, or click the
run button.

You’ll see that the line we’ve just run pops up in the console, along
with the output from the command we’ve just given R. If you run an
incomplete command, R will wait for you to complete it:

``` r
1 + [Ctrl + Enter]
```

Note that the \> in the console window is now a + indicating that are is
waiting for the command to be completed. You can exit commands by
pressing escape within the console window.

When using R as a calculator, the order of operations is the same as you
would have learned back in school. From highest to lowest precedence:

  - Parentheses: ( )
  - Exponents: ^ or \*\*
  - Divide: /
  - Multiply: \*
  - Add: +
  - Subtract: -

So for example we can try:

``` r
3 + 5 * 2
```

versus

``` r
* (3 + 5) * 2
```

*Note that R will ignore spaces between + and - , etc.*

**Mathematical functions**

R has many built in mathematical functions. To call a function, we
simply type its name, followed by open and closing parentheses. For
example:

``` r
log(1)  # natural logarithm
log10(10) # base-10 logarithm
exp(0.5) # exponent
```

The text after each line of code is called a “comment”. Anything that
follows after the hash (or octothorpe) symbol \# is ignored by R when it
executes code.

**Variables and assignment**

We can store values in variables using the assignment operator`<-`,
which is the less than sign followed by a minus like this:

``` r
x <- 1/40
```

*Note: R does not print the value, but x now contains the value 0.025, *
*Note: Will see that x has been loaded in to the environment.*

And we can now perform calculations using x in place of our original
number. For example, take the natural log:

``` r
log(x)
```

We can also reassign variables that we have created. Let make x have a
value of 100:

``` r
x <- 100
```

We can also update the assigned value by including the variable we want
to update. E.g.:

``` r
x <- x + 1
```

and even:

``` r
y <- x * 2
```

Variable names can contain letters, numbers, underscores and periods.
They cannot start with a number nor contain spaces at all. Different
people use different conventions for long variable names, these include:

  - periods.between.words
  - underscores\_between\_words
  - camelCaseToSeparateWords

What you use is up to you, but be consistent.

    What will be the value of each variable after each statement in the following:
    
    mass <- 47.5
    age <- 122
    mass <- mass * 2.3
    age <- age – 20

### Vectorization

R is vectorized: variables and functions can have vectors as values. A
vector in R describes a set of values in a certain order of the same
data type. For example:

``` r
1:5 
```

Produces a vector of numbers. And we can perform mathematical functions
on this vector:

``` r
2^(1:5)
```

Notice that what R has done here is raise 2 to the power of each number
in the vector.

We can also perform arithmetic on multiple vectors, for example

``` r
x <- 1:4
y <-  5:8
x + y
```

## R Packages

It is possible to add functions to R by writing a package, or by
obtaining a package written by someone else. Packages are generally
written to perform specific functions or statistical analyses, or for
manipulating specific types of data.

R comes with some packages pre-installed, and we can see what packages
are installed by typing:

``` r
installed.packages()
```

You can see I have a lot of them and can’t even see the entire list…
This will happen when your output is too large to be seen in the
console, and is NB to bear in mind when working with large datasets.

Most packages are available via CRAN: **The Comprehensive R Archive
Network** You install packages by typing
`install.packages("packagename")`, where packagename is the package name
in quotes.

These packages are often getting updated, especially as new versions of
R come out, and you can update them via `update.packages()`.

Another key feature is making the library available for use. You can do
this through the packages tab, but it is more reproducible to put this
into your script. Often people will put this at the top of the script so
that you can quickly make sure that you have all of the packages you
need to run the code: To load a package we type:

``` r
library(car)
```

*Note: The library package name only works when you have that package
installed, and note that the package name here doesn’t need to be in
quotations like it does when you install the package. * <br> *Note: Once
a package is installed, it doesn’t need to be installed again*

Multiple packages can be loaded or installed by putting them into a
string. This is done using the incredibly useful concatenate function,
`c()`. For example, you can install `dyplr` and `ggplot2` using:

``` r
install.packages(c("dplyr", "ggplot2"))
```

    Install the following packages: 
    
    "ISLR", "ggplot2", "GGally", "dplyr", "cowplot", "mice"
    
    And load them to make them available in the current session.

## Exploring dataframes

Most of the time when we are working in R, we will be working with data
that are in the form of dataframes. This data will usually be imported
into R from a spreadsheet or text file.

Many packages also include data that we can use as templates for our own
data and analyses. For example, we will explore data in a dataframe that
comes pre-installed with R.

``` r
data("iris")
```

We can begin by getting a sense of the structure of the dataframe. To
start let’s see what the data look like by clicking on the dataframe in
our environment window. Clicking on it will open a new tab showing the
data as we’d see it in a spreadsheet. A more reproducible way to do this
would be to call the head of the dataframe:

``` r
head(iris)
```

Here we see that the dataframe has 14 columns. The function `head()` has
pulled up the first 6 rows.

We can see more information about each variable using the `str()`
function

``` r
str(iris)
```

Now we see that `iris` is a dataframe with 150 observations (or rows)
and 5 variables (or columns). We also se a description of each variable.
Here we see that we have numeric variables and `Species` which is
labeled as a factor. Factors are categorical variables, similar to
characters.

Here are a few functions we can use to get a sense of our data
structure:

``` r
nrow(iris)
ncol(iris)
dim(iris)
```

We can also index individual variables by using the dollar sign, `$`.
For example to select the **Species** variable we can use:

``` r
iris$Species
```

## Plotting data with ggplot2

A large component of analysing data, including exploratory data
analysis, is using data visualization. Plotting data can be done in base
R, and this is what many packages will use. For example, we can plot
**sepal length** against **sepal width** using the built-in `plot()`
function:

``` r
plot(iris$Sepal.Length, iris$Sepal.Width)
```

Note that we are specifying the data to use using the name of the
dataframe (iris), and the ‘$’ to specify the columns. While this plot
was very easy to produce, it is not the most appealing figure (I
wouldn’t want to put this in a publication). There are a number of
things we could do to improve it: change the axis labels, color the
points by species, add trendlines, etc. All of this is possible to do in
base R, but we will do this using functions in `ggplot2`.

### The grammar of graphics

ggpplot2 is build on the ‘grammar of graphics’ (hence ‘gg’).
Essentially, this is a framework which follows a layered approach to
describe and construct visualizations, or graphics in a structured
manner. This means that plots are constructed from different types of
layers, all of which can be modified and customized.

Let’s start by reproducing the plot from before in ggplot. This plot is
a scatterplot, so we will use the `geom_point()` plot type.

``` r
library(ggplot2)
ggplot(data = iris, aes(x = Sepal.Length, y = Sepal.Width))+
  geom_point()
```

In the first row we have specified the dataframe to use (iris), as well
as the aesthetics of the plot, in this case the variables to use for the
x and y axes. This is the first layer of your plot Each of these (data
and aes) are **arguments** *within* the `ggplot()` function. The second
row tells us the second layer we want to add. In this case, a
scatterplot layer. We have to finish this line with the open and closed
parentheses because `geom_point()` is an arugument. Here we are not
changing any arguments. We combine the two rows using the ‘+’ sign.

Now let’s make some of those changes we mentioned above. First the axis
labels. These can be thought of as an additional layer. The ggplot2
default is to use the names of the variables as they appear in the
dataframe. Let’s remove the ‘.’ and include the measurment unit:

``` r
ggplot(data = iris, aes(x = Sepal.Length, y = Sepal.Width))+
  geom_point() + 
  xlab("Sepal Length (cm)")+
  ylab("Sepal Width (cm)")
```

Note that we still specify the variable names how they appear in the
dataframe, and we place the *labels* in quotes.

How about adding some color and trendlines for each species?

``` r
ggplot(data = iris, aes(x = Sepal.Length, y = Sepal.Width, 
                        color = Species))+
  geom_point() + 
  xlab("Sepal Length (cm)") +
  ylab("Sepal Width (cm)") + 
  geom_smooth(method = "lm")
```

Maybe we don’t like the background, so we can change the plotting theme
(i.e., add another layer):

``` r
ggplot(data = iris, aes(x = Sepal.Length, y = Sepal.Width, 
                        color = Species))+
  geom_point() + 
  xlab("Sepal Length (cm)") +
  ylab("Sepal Width (cm)") + 
  geom_smooth(method = "lm")+
  theme_classic()
```

Now this plot is looking more like something we could put into a report
or a paper\!

    Use ggplot2 to make a plot of petal length vs petal width. 
    Relable the axes, inlcuding units (cm).
    Color the points by species, and include a separate trendline 
    for each species.

## Seeking help

R and any package you load have help files. There are a few ways to
access help within R and RStudio:

  - `?function_name`
  - `help(function_name)`

You can also use a fuzzy search by typing `??` for example:

``` r
??read.ta
```

**Special Operators** <br> You can also get help on special operators,
like the assignment operator. Let’s try typing:

``` r
?”<-“
```

Many packages also contain **VIGNETTES**, or tutorials and extended
examples. If we type:

``` r
vignette()
```

without any arguments, we will see a list of all vignettes for the
installed packages.We can also specify a particular packge:

``` r
vignette(“dplyr”)
```

*Note: we use quotes here*

**When you have no idea where to begin** <br> If you don’t know what
function or package you need to use CRAN Task Views is a list of
packages grouped into fields.<br>

Also *Stack Overflow* can be very helpful. Remeber to use the \[r\] tag
for your question. There are very specific formats for questions on
these types of sites; it is suggested that you use the functions below
to help get the information people seeing your question might need.

``` r
?dput
sessionInfo()
```

-----
