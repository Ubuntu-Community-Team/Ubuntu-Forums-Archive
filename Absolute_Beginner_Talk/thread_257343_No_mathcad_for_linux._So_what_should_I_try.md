---
title: "No mathcad for linux. So what should I try?"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-09-14
I found out that the math program mathcad doesent work for linux. So can anyone suggest me some other kind of math program?

---

### Post by ape on 2006-09-14
What about Mathmatica, Maple or Matlab?  I believe that there are linux versions of these programs out there.

---

### Post by charles.g.moore on 2006-09-14
im not sure if this will help but check this out:

[http://www.cinlug.org/node/308](http://www.cinlug.org/node/308)

---

### Post by Ubuntist on 2006-09-14
I'm not familiar with Mathcad, but according to Wikipedia it is similar to Maple and Mathematica, either of which may have a Linux version.

You could also have a look at the open-source packages octave and scilib.  I don't think they're quite as swish as mathcad seems to be, but they might do.

Another possibility: install a Windows emulator like wine and run Mathcad from there.

---

### Post by &#12465;&#12452;&#12488; on 2006-09-14
There's a Free program called [Maxima](http://maxima.sourceforge.net/), but I'm not sure if that's exactly what you're looking for.

---

### Post by Najand on 2006-09-14
> **&#12465 said:**
> There's a Free program called [Maxima](http://maxima.sourceforge.net/), but I'm not sure if that's exactly what you're looking for.

Just checked it, Sounds nice.... I am going to give it a try. Thanks &#12465;&#12452;&#12488;&#12373;&#12435;&#12290;

---

### Post by Marsolin on 2006-09-14
I'm not sure what kind of math capabilities you need, but you could check out [OpenEuclide]("http://linuxappfinder.com/package/openeuclide"). It is 2D geometry program.

---

### Post by Najand on 2006-09-14
There is also a software  called Scilab, which is GNU alternative for Matlab... If you are looking for a numberical calculation software, it can be used.

---

### Post by derjames on 2006-09-14
What about 'Octave'?...

by the way, please read this article from linux.com

cheers

[http://www.linux.com/article.pl?sid=06/09/06/1548258](http://www.linux.com/article.pl?sid=06/09/06/1548258)

---

### Post by acmethunder on 2006-09-18
I have tried Maxima (with no luck getting wxMaxima to work), Octave, and I am thinking about Scilab.  The problem is that there does not seem to be anything that has a good GUI for the gnome desktop.  Everything seems to be for KDE.  Is there a good clean GUI for either Maxima or Scilab (that is easy to install), or should I go for KDE.

---

### Post by Rui Pais on 2006-09-19
hi,
Mathcad and Mathematica are **symbolic** math applications, while Maple and Mathlab are **numeric** math apps. One must check what in fact needs!

Symbolic math apps for linux are Maxima, Axiom and Mathematica (not-free). There is another thing free but not open-source (requires a registration) but i forget the name. 

A good front end for Maxima, for those who can't buy Mathematica, is an app call TexMacs (apt-get install texmacs). 
It works as an excellent GUI for several other apps/languages like python, shell, octave, gnuplot or maxima (much better then xMaxima!). 
As far as i remember, to work as a GUI to maxima you only need to have both installed. 

Numeric math open-sources apps, are scilab or octave. Again Texmacs could be used as a GUI for the last.

---

### Post by egoldtech on 2006-09-19
AFAIK  there is no other software as powerfull as Matlab to make numerical calculation, numerical modelling , analytical & numerical solution of equations.
if you need something good looking to make presentations, take a look of the Latex. 
if you need something powerfull to make calculation look for matlab and all its modules.

best regards

---

### Post by dimis on 2006-10-06
Just for the record. Maple is the king on **symbolic** computation. But as others have already said, it depends on what you want to do with a program like that. Most common use of Matlab (for educational purposes) is signal processing. Most common use of Maple (for educational purposes) is algorithmic algebra (i.e. root isolation, polynomial [symbolic] system solving, resultants, ideals, ... ---> _symbolic_ computing). 
If you simply want to draw charts or functions you can help yourself with GNUPlot and export output in many formats (among others jpg, eps, fig) :)

---

