---
title: "Ubuntu study program?"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Belathor on 2006-05-21
Hi,

I am in university and use my computer to study for my classes. On Windows, I use a program called [Recallplus]("www.recallplus.com") to review my study material. It has been a great help to me and would like to know where I could find a similar program for Linux, or since I have been very unsuccessful so far in finding such a program, where can I attract the attention of programmers to make such a program for linux?

Thanks!

---

### Post by rado_london on 2006-05-21
Hey a bit of offtopic. This program looks cool. I am at college and such thing would be helpful as my schedule is busy. Comeone people help us!

---

### Post by aysiu on 2006-05-21
Apparently, there are study tools for Japanese and the Bible: ```
 apt-cache search study
kverbos - Spanish verb form study application for KDE
perlsgml - tools to build and analyze SGML or XML document type definitions.
tagcoll - Commandline tool to perform operations on tagged collections
ttf-gentium - Gentium TrueType font
avida-base - Auto-adaptive genetic system for Artificial Life research
bibletime - A bible study tool for KDE
bibletime-i18n - Translated messages and documentation of BibleTime.
evolver - Surface Evolver
evolver-doc - Surface Evolver documentation and examples
fastlink-doc - [Biology] Some papers about fastlink
gnomesword - Bible study with GNOME
gvr - Interactive, introductory programming language
gvr-lessons - Interactive, introductory programming language lessons
kiten - Japanese reference/study tool for KDE
libkiten-dev - development files for Kiten library
libkiten1 - library for Kiten Japanese reference/study tool
libmath-combinatorics-perl - Perform combinations and permutations on lists
matrem - An experiment in Artificial life
mesademos - Example programs for Mesa (and OpenGL in general)
mpb - MIT Photonic-Bands
mpb-doc - MIT Photonic-Bands documentation
mpb-mpi - MIT Photonic-Bands, parallel (mpich) version
perspic - A text indexing and word search program
perspic-texts - Some pre-indexed texts for perspic
regina-normal - 3-manifold topology software with normal surface support
snappea - a program for creating and studying hyperbolic 3-manifolds
snappea-dev - development files for SnapPea hyperbolic 3-manifold tool
sword-comm-pers - Personal Commentary for SWORD
tessa - simulation of 3D optical systems with the FDTD method
tessa-mpi - simulation of 3D optical systems using FDTD on LAM-MPI clusters
uligo - tsumego (go problems) practice tool
abs-guide - The Advanced Bash-Scripting Guide
sgb - The Stanford GraphBase: combinatorial data and algorithms
``` Maybe your Windows program could work in Wine? [http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by Belathor on 2006-05-21
Thanks for suggestion Aysiu. I'll try to see if I can get it working.

It still would be great to have an open source version of this class of software, it is so useful, especially for people with busy schedules (which happens to be just about everybody!).

EDIT: It doesn't work. It requests an activex control which it downloads but can't install. All the more need for an open source version!

---

### Post by adamkane on 2006-05-21
It's been many years we've all been waiting for a decent study tool for KDE or Gnome.

For now, there are some java and php/mysql options, if you search freshmeat.net.

This seemed to be the most featureful that I could find:
[http://memorize-words.sourceforge.net/]("http://memorize-words.sourceforge.net/")

You need to install Java this way:
[http://easylinux.info/wiki/Ubuntu#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox]("http://easylinux.info/wiki/Ubuntu#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox")

Download file to desktop, create a folder called memorize-words, move file into new folder, and extract.

Then:
```

cd ~/Desktop/memorize-words
java -jar memorize-words.jar

``` 
It's technically a word learning program, but it is useful for any text or pictures.

It would be nice to find a program that handles formulas though.

Creating your own PHP/MySQL study aid (basically a web page that spits out some content, and even checks your responses) would be rather straightforward to create/implement.

---

### Post by Belathor on 2006-05-22
thanks adamkane! Although all I've managed to get out of memorize-words is a nice pretty blank white box, I'm sure after I finally get the program up and running it will be a lot better than nothing!

---

### Post by adamkane on 2006-05-22
Wyneken also seems interesting. It's a notebook organizer that uses latex, where you can include formulas and pictures. It doesn't help you memorize though.

[http://www.99b.org/wyneken/]("http://www.99b.org/wyneken/")

To get it working install kile (to obtain tetex), and install pysqlite2:
```

sudo apt-get install kile python2.4-pysqlite2

``` 
Download wyneken to your desktop and extract. 

Then:
```

cd ~/Desktop/wyneken-0.4_beta5
sudo python install.py
sudo wyn --auto-config

``` 
You then need to create a new panel entry for wyneken or run it manually. If you decide to install wyneken, and have any problems, let us know.

The wyneken website has a user manual, which you will need, in order to do anything useful with the program:
[http://www.99b.org/wyneken/users-guide.pdf]("http://www.99b.org/wyneken/users-guide.pdf")

---

### Post by adamkane on 2006-05-22
If you want to do any equation editing and solving, check out TeXmacs + Maxima:
[http://arxiv.org/html/cs.SC/0504039]("http://arxiv.org/html/cs.SC/0504039")

This looks like a good replacement for MacKichan Scientific Workplace/Notebook or Mathematica/Maple/Matlab.

---

### Post by rolf_lindberg on 2006-07-30
Have you tried schoolbell? It's in the repos, but it's a calendar/personal planner thing, maybe not what you were after?

---

### Post by adamkane on 2006-07-30
Schoolbell looks like a LAMP CMS (Linux/Apache/Mysql/PHP Content Management System). 

There is another LAMP CMS called Moodle that allows you to create interactive quizzes in addition to other activities. It's very useful, but it's meant for organizations. 

You have to install LAMP first, then install a version of Moodle that works with the version of LAMP you have installed. There's always issues with folder permissions with new LAMP installations, but they are not difficult to fix. 

After you install Moodle, you have to create an administrator, at least one teacher, and at least one student. Then you have to figure out how to create your first set of exercises or quizzes.

It's straight forward, but you will need some patience, if this is your first LAMP installation.

---

### Post by Lord Illidan on 2006-07-30
I haven't tried it myself, but what about kdissert?

---

### Post by adamkane on 2006-07-30
More info about kdissert and mind maps:
[http://dot.kde.org/1129372863/](http://dot.kde.org/1129372863/)

It looks like mind maps are just glorified outlines, but the benefit is that you can easily add new sections to your outlines with a graphical mind map.

---

### Post by nalmeth on 2006-07-30
Hmm, it seems that there are functional programs, but you have to use many different apps at a time.

It would be cool to see a project like a "Students Edition" of Ubuntu, or an addon like Ubuntu Studio which gives you a launcher for all the related apps.

Going back to school in the fall, would be pretty useful I should think

EDIT: I KNOW ABOUT EDUBUNTU

I'm thinking more along the lines of an OS (or addon) tailored more to college students specifically

---

### Post by T700 on 2006-07-30
Just installed Kdissert.  Awesome program!  I'm really happy to have found out about this.  

Paul

---

### Post by Dr. Cox on 2006-08-08
i don't like kdissert too much. what i am looking for is something like free mind (too bad i am too much of an idiot to get it installed)... i would like to  have a mindmap program with not only subdependencies but also horizontal connections between different "arms" if you know what i mean

---

### Post by AndThenWhat on 2008-05-29
> **Belathor said:**
> Hi,

I am in university and use my computer to study for my classes. On Windows, I use a program called [Recallplus]("www.recallplus.com") to review my study material. It has been a great help to me and would like to know where I could find a similar program for Linux, or since I have been very unsuccessful so far in finding such a program, where can I attract the attention of programmers to make such a program for linux?

Thanks!
[http://www.linux.com/articles/43409](http://www.linux.com/articles/43409)

---

