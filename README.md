# Introduction To Python and Data Science
_LSE &mdash; Department of Statistics &mdash; Spring Term 2019_

Welcome! This is the page for the *Introduction To Python and Data Science* course. Here you will find the course material, as well as instructions for setting up Python on your computer.

## Table of Contents
- [The First Lecture](#the-first-lecture)
  - [A bit of Admin](#a-bit-of-admin)
  - [Setting up Python and Jupyter Notebooks](#setting-up-python-and-jupyter-notebooks)
- [Lecture Worksheets](#lecture-worksheets)
- [Questions?](#questions)
  - [A Selection of Your Questions](#a-selection-of-your-questions)
    - [I. Numbers, Truncation and Babylonians: Arithmetic in Python](#i-numbers-truncation-and-babylonians-arithmetic-in-python)
      - [The choice of initial guess](#the-choice-of-initial-guess)
      - [Printing Text](#printing-text)
      - [Indentation](#indentation)

## The First Lecture
> Two Babylonians walk into a bar...

### A bit of Admin
- **Attendance Register:** Please sign your name on the sheet at the front of the class.
- **Post-its:** As you come into the class, you will find green and orange post-it notes next to the register sheet; please take one of each. You will use these during the class exercises to tell me how you are doing:
  - A *green* post-it stuck to your laptop means you have completed the exercise and are happy for the class to continue.
  - An *orange* post-it stuck to your laptop means you have a question and want me to take a look at your code.
  - No post-it means you are still working on it.

### Setting up Python and Jupyter Notebooks
We will be using the latest stable version of Python 3 for the course --- this is Python 3.7 at the time of writing. Follow these steps to set up everything you will need in a couple of minutes:
1. Download [Anaconda](https://www.anaconda.com/download/). Make sure to choose the 3.7 version!
2. Execute the installer and follow the default steps. This might take a little longer.
3. In the meantime, download the first notebook from this page. Notebooks have the file extension `.ipynb`.
4. Once the Anaconda installation finishes, find the **Jupyter Notebook** app. Alternatively, you can run `jupyter notebook`on your system's command line. The notebook browser should open automatically.
5. Navigate the browser to the notebook you just downloaded and open it. You're ready to go!

## Lecture Worksheets
We will use Jupyter Notebooks for the majority of the course. Each worksheet will be released on this page shortly before the start of the lecture. You should download the worksheet and follow along &mdash; the only way to learn programming is by doing! Nonetheless, a completed worksheet will also be released after the lecture.

## Questions?
> Ask, and it will be given to you; seek, and you will find; knock, and it will be opened to you.

Ask me! You can ask me during lectures, during excercises, or at the end of each class. You can also email me at [r.bailo@imperial.ac.uk](mailto:r.bailo@imperial.ac.uk) if you have questions during the week. I will try to answer short questions promptly; if the question is longer or particularly interesting we might discuss it in class instead.

### A Selection of Your Questions
Here are some questions I have received so far; you might find the answers useful.

#### I. Numbers, Truncation and Babylonians: Arithmetic in Python

##### The choice of initial guess
*In the Babylonian square root algorithm, where we estimate the square root of a number `s`, why do we begin by letting `x=s`?*

The Babylonian square root algorithm is an iteration. We begin with a guess `x`, and then use an update step `x=(x+s/x)/2` which improves the quality of the guess. As we saw in class, the convergence of the algorithm is extremely good, so much so that it does not really matter what initial guess we take &mdash; it will converge to the answer in just a few iterations. Taking `x=s` is just a possible choice, but letting `x=s/2` or `x=1` would work just as well.

Later in the course we will see examples of other algorithms: some which only converge well if the initial guess is a good one, some which converge to different things depending on what guess we take, and some which never converge well at all!

<hr>

##### Printing Text
*In the completed worksheet I found the command `print("Difference: "+str(difference))`. What does the `str` function do?*

We will see text handling in detail very soon, but in the meantime: The function `print` displays text output: evaluating `print("Hello World")` would display "Hello World" to the console. However, Python can only display text! If we let `x=1.0`, `x` cannot be displayed directly because its type is `float`. When calling `print(x)`, Python is secretly executing `print(str(x))` instead, converting the `float` to text (a `string`) and *only then* displaying something.

If, rather than printing just a number, we want to annotate the output, we must resort to fancier tricks. The `+` operator represents addition for the `int` and `float` types, but it represents `string` concatenation as well. In order to print `The number is 1.0`, I have to concatenate the strings `"The number is "` and `"1.0"`. Executing
```python
print("The number is "+1.0)
```
fails catastrophically because Python does not know how to put together a `string` and a `float`. Running instead
```python
print("The number is "+str(1.0))
```
does the trick!

<hr>

##### Indentation
*I tried writing the `babylonianRoot` function:*
```python
def babylonianRoot(s, n):
    x=s
    
    for k in range(0,n):
    xNext=(x+s/x)/2
    print("Difference: "+str(abs(xNext-x)))
    x=xNext
    
    return x
```
*However, python throws an error: `IndentationError: expected an indented block`. What has gone wrong?*

Indentation is crucial in Python! You have indented most of your code once, indicating that it belongs inside the function block `def babylonianRoot(s, n):`. However, you have not indicated which parts of the code belong inside the `for` loop. Double indentation is needed for those parts: 

```python
def babylonianRoot(s, n):
    x=s
    
    for k in range(0,n):
        xNext=(x+s/x)/2
        print("Difference: "+str(abs(xNext-x)))
        x=xNext
    
    return x
```
<hr>
