---
title: "Generating graphs and plots from MySQL database"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by sgfaulkner on 2007-02-06
I have been using ubuntu for a bit now on several computer and linux for the past 6 months.  I feel fairly comfortable in the environment, but now I have a new challenge.  I work at a company that just finished a very large project that ran for several straight months.  During that time, all of the data that was acquired(variables like, loads, pressures, depths, temperatures) was stored into a mysql database.  I need to be able to access that data and generate things like graphs and plots of various variables.  We have some basic tools that were programmed in house with python, but they aren't very robust and can't be customized at all.  Can anyone recommend a program or utility in linux that might be able to do what I am looking for?

Note, I also have no experience in mysql database management or python programming, I just know what they are and what they do.

---

### Post by dupa on 2007-02-07
> **sgfaulkner said:**
> I have been using ubuntu for a bit now on several computer and linux for the past 6 months.  I feel fairly comfortable in the environment, but now I have a new challenge.  I work at a company that just finished a very large project that ran for several straight months.  During that time, all of the data that was acquired(variables like, loads, pressures, depths, temperatures) was stored into a mysql database.  I need to be able to access that data and generate things like graphs and plots of various variables.  We have some basic tools that were programmed in house with python, but they aren't very robust and can't be customized at all.  Can anyone recommend a program or utility in linux that might be able to do what I am looking for?

Note, I also have no experience in mysql database management or python programming, I just know what they are and what they do.


without programming, the only thing you can do, is to copy & paste your data in a openoffice calc, and create graph there.

otherwise, you should learn SQL and a programming language, such PHP (or java too) and use its libraries to create graph/charts.

---

### Post by firefly2442 on 2007-02-07
Gnuplot works well:

[http://en.wikipedia.org/wiki/Gnuplot](http://en.wikipedia.org/wiki/Gnuplot)

:)

---

### Post by indytim on 2007-02-07
PHP with the GD2 library will do it.  JpGraph is the graphing package I use to handle graph generation from a MySQL server.

Will need to get up to speed on PHP and then gain familiarity with the extensive library functions associated with JpGraph.  Worth the journey if this is a re-occurring event.

IndyTim

---

