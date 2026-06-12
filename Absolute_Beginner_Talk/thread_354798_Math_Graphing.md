---
title: "Math Graphing"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by ayed on 2007-02-06
Hello All,
I need a software that can do graphical solving of equation, scatter plots, linear, and quadratic plots. Does anyone know of a software available for Ubuntu 6.10?
Thanks

---

### Post by in_flu_ence on 2007-02-06
maxima? I haven't used this personally but I think it might work for u.

---

### Post by meng on 2007-02-06
gnuplot
It's worth playing around with, although it runs from the terminal.

---

### Post by ghandi69_ on 2007-02-06
I know this is not the best answer to your question, but I know MATLAB does those things, and at my University they only have MATLAB on the unix workstations... so it can run under linux..... but thats all I know.

---

### Post by ayed on 2007-02-06
I need something graphical interface, and if you guys could tell me how to compile it?
Thanks A LOT!

---

### Post by olejorgen on 2007-02-06
gnuplot can do at least some of them

ups, beaten :P

---

### Post by IYY on 2007-02-06
There are many such programs in the repositories. Personally, I use graphmonkey, but I picked it randomly. Anyway, it does what I need it to, graphically, and is in the repositories.

---

### Post by meng on 2007-02-06
I already recommended, but gnuplot is very easy to use, even though it runs in a terminal. Check out the website:
[http://www.gnuplot.info/](http://www.gnuplot.info/)
You don't have to be afraid of a program just because it doesn't have a GUI.

---

### Post by Rui Pais on 2007-02-06
Or you can try octave or scilab. They extend the graphical capacities of gnuplot with numerical calculation that may be what you are looking for (solving equations graphically and/or numerically for example) Both use gnuplot on the backwards for graphical contents. And they have a GUI interface, although octave one is very kde oriented. it's called, of course, koctave.

Maxima, an already suggested, is more simbolic calculation oriented, but it have a good graphical support too and it have a basic gui called xMaxima. 

All, gnuplot, maxima and octave can be used as plugins inside an scientific editor called TeXmacs, that act as a (basic) gui for them - something like Mathematica notebook. The plugins can be used all simultaneously on same doc (and with few others mathematical plugins) plus you have an excellent editor of high quality, that can produce pdf, ps or tex :)
[here is a good tutorial]("http://arxiv.org/html/cs.SC/0504039") with images to get an idea of how it is...

If you want a very deep graphical exclusively oriented app the most powerfull around are (i think) [scigraphica]("http://scigraphica.sourceforge.net/index.html"), [labplot]("http://labplot.sourceforge.net/") and [kmatplot]("http://kmatplot.sourceforge.net/"). 

[Here ]("http://www.linux.com/howtos/Scientific-Computing-with-GNU-Linux/index.shtml")is a descriptive list of scientific apps on Linux. [Chapt. 6]("http://www.linux.com/howtos/Scientific-Computing-with-GNU-Linux/graphvis.shtml") is all on graphics and data visualization.

hth

---

