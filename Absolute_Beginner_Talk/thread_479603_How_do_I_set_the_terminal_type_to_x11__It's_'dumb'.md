---
title: "How do I set the terminal type to x11?  It's 'dumb' right now."
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by akellehe on 2007-06-20
Hey, I'm sort of new to ubuntu but I've managed to install gnuplot and have it working. There is a problem... Whenever i give it a plot command it plots in the terminal using asteriks and + signs and - signs and actually DRAWS a plot with them. I would kind of rather have a graphical plot outside the terminal window.

I think the root of my problem is: my "terminal type is set to dumb" as it says when I run the gnuplot command. How do I set the terminal type to x11?

---

### Post by nylecoj813 on 2007-06-20
> **akellehe said:**
> Hey, I'm sort of new to ubuntu but I've managed to install gnuplot and have it working. There is a problem... Whenever i give it a plot command it plots in the terminal using asteriks and + signs and - signs and actually DRAWS a plot with them. I would kind of rather have a graphical plot outside the terminal window.

I think the root of my problem is: my "terminal type is set to dumb" as it says when I run the gnuplot command. How do I set the terminal type to x11?

I'm not at all familar with gnuplot, but in case you haven't searched around google:

[http://www.gnuplot.info/docs/node442.html](http://www.gnuplot.info/docs/node442.html)
[http://t16web.lanl.gov/Kawano/gnuplot/intro/basic-e.html#set](http://t16web.lanl.gov/Kawano/gnuplot/intro/basic-e.html#set)
(and there's a lot of other results too)

Both seem to say to use the command: set terminal x11

See if that works? Otherwise, we'll have to see if there's someone who actually uses gnuplot to help ;)

---

