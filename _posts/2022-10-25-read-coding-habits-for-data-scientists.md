---
layout: post
title: 'Read: Coding habits for data scientists (and anyone else who codes)'
date: 2022-10-25 01:40 +0800
---

[This](https://www.thoughtworks.com/insights/blog/coding-habits-data-scientists) is an excellent article listing and explaining useful coding habits for data scientist (or anyone who codes really). In this post, I'll highlight some of the most pertinent lessons:

## Turn complex code into functions

> What did we gain by abstracting away the complexity into functions?
> -   **Readability**. We just have to read the interface (i.e. categorize_column()) to know what it’s doing. We didn’t have to read each line or search the internet for things that we don’t understand (e.g. pd.qcut). If I still didn’t understand what the function did based on its name and usage, I can read its unit tests or its definition.
> -   **Testability.** Because it’s now a function, we can easily write a unit test for it. If we accidentally change its behaviour, the unit tests will fail and give us feedback within milliseconds.
> -   **Reusability.** To repeat the same transformation on any column (e.g. ‘Age’, or ‘Income’), we just need one line (not seven lines) of code.

This lesson is worth repeating especially for beginners. When starting out, we're less likely to write anything complex so we think we can get away with not encapsulating our codes in functions. But, as complexity increases, our ability to keep up with it diminishes and we'll begin to see the importance of abstracting complexity into functions.

It's important to learn that lesson now rather than later.

## Jupyter notebooks are good for prototyping but don't stay there for too long


> In interior design, there is a concept (the “Law of Flat Surfaces”) which states that "any flat surface within a home or office tends to accumulate clutter." Jupyter notebooks are the flat surface of the ML world. 
> 
> Sure, Jupyter notebooks are great  for quick prototyping. But it's where we tend to put many things — glue code, print statements, glorified print statements (df.describe() or df.plot()), unused import statements and even stack traces. Despite our best intentions, so long as the notebooks are there, mess tends to accumulate. 
> 
> Notebooks are useful because they give us fast feedback, and that’s often what we want when we’re given a new dataset and a new problem. However, the longer the notebooks become, the harder it is to get feedback on whether our changes are working. 
> 
> In contrast, if we had extracted our code into functions and Python modules and if we have unit tests, the test runner will give us feedback on our changes in a matter of seconds, even when there are hundreds of functions.  
> 
> Hence, our goal is to move code out of notebooks into Python modules and packages as early as possible. That way they can rest within the safe confines of unit tests and domain boundaries. This will help to manage complexity by providing a structure for organizing code and tests logically and make it easier for us to evolve our ML solution.  So, how do we move code out of Jupyter notebooks?

This one surprised me at first but it started to make more sense later on as I worked with Jupyter more. As mentioned by the writer, Jupyter is great for prototyping; I would even say that it's also great for complete projects provided that they are small. For larger projects, it's best to export your code somewhere else once you've fiddled enough with the data set in a Jupyter notebook.

The following image is a great illustration of the whole process of exporting code out of Jupyter:

![Jupyter notebook refactor cycle](https://pocket-image-cache.com//filters:format(jpg):extract_focal()/https%3A%2F%2Fwww.thoughtworks.com%2Fcontent%2Fdam%2Fthoughtworks%2Fimages%2Fphotography%2Finline-image%2Finsights%2Fblog%2Fdata-engineering%2Fblg_inline_coding_habits_data_scientists_02.png)


One thing the writer left out is Jupyter is also used for publishing findings in the form of code plus narrative format. Once a project is complete and everything is finalised, it might be a good idea to import back the complete code into a Jupyter notebook so we can accompany our codes with storytelling.

## Make small and frequent commits

> When we make small and frequent commits, we get the following benefits:
> -   Reduced visual distractions and cognitive load.
> -   We needn’t worry about accidentally breaking working code if it’s already been committed.
> -   In addition to [red-green-refactor](https://blog.cleancoder.com/uncle-bob/2014/12/17/TheCyclesOfTDD.html), we can also [red-red-red-revert](https://www.facebook.com/notes/kent-beck/one-bite-at-a-time-partitioning-complexity/1716882961677894/). If we were to inadvertently break something, we can easily fall back checkout to the latest commit, and try again. This saves us from wasting time undoing problems that we accidentally created when we were trying to solve the essential problem.

A nice list of benefits on why commits should be small and frequent. I also like how the writer answer the question of how small a commit should be:

> So, how small of a commit is small enough? Try to commit when there is a single group of logically related changes and passing tests. One technique is to look out for the word “and” in our commit message, e.g. “Add exploratory data analysis and split sentences into tokens and refactor model training code”. Each of these three changes could be split up into three logical commits. In this situation, you can use **[git add --patch](https://nuclearsquid.com/writings/git-add/)** to stage code in smaller batches to be committed.

I've never used `git add --patch` before. I want to try that in my next commit.

Cheers.