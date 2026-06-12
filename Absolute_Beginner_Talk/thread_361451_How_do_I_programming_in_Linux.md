---
title: "How do I programming in Linux?"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Unlockitall on 2007-02-14
i want to learn to program, so linux is a good choice because of all the free tools. so i have xubuntu running on my computer, and it comes with some useful tools, but i dont know how to get them open and use them. anyone know how to?

---

### Post by black_ice on 2007-02-14
what is the kind of prgramming u mean ..... ? 

php and other web development stuff 

or java and other Desktop programming ??

---

### Post by dannyboy79 on 2007-02-14
i would suggest looking thru the programming section of this forum, then decide which program you'd like to start with first, C++, python, java, perl, there are TONS of different programming langauges. here is a link to the programming section: [http://www.ubuntuforums.org/forumdisplay.php?f=39](http://www.ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by steve.horsley on 2007-02-14
The tools you use depend to an extent on the language you are learning, Have you chosen a language to learn yet? I think python is an easy language to get started with, but I haven't seen that much good tutorial material for it. Java is a good language, and Sun's java tutorial ([http://java.sun.com/docs/books/tutorial/index.html](http://java.sun.com/docs/books/tutorial/index.html)) will take you a very long way and is pretty-much complete.

---

### Post by Unlockitall on 2007-02-14
python, sorry, i thought i put it in the first post

---

### Post by Unlockitall on 2007-02-14
anyone know what programs i need for python programming?

---

### Post by Unlockitall on 2007-02-14
please help...:(

---

### Post by kebes on 2007-02-14
The basic tools for python programming are already included in Ubuntu. You can run "python" on the commandline to run python programs you've written. To write the program, you just need a text editor. Many text editors do syntax-highlighting, which helps with programming.

If you want to make graphical applications, then you can use "QT Builder" to build application frameworks, and then "pyuic" (part of PyQT tools) to transform those frameworks into python code.


If you're new to programming, the best place to start is doing a simple python tutorial (there are many on the web). As I said, all you need is python (already installed) and a text editor.

---

### Post by Unlockitall on 2007-02-14
thank you soooooooo much!!!!!!!!!!!!!!!!!!!!!
:guitar: :popcorn: :KS :) :guitar: :popcorn: :guitar:

---

### Post by steve.horsley on 2007-02-15
I've been coding in python for a couple of years, just using the gedit text editor. I haven't had to write a python GUI yet, though. If you want to do that, I have heard good things about glade - google for it. Python is included in the default Ubuntu install - lots of the utilities use python.

I recently had a quick look at an editor called geany (there is an Ubuntu package for it) and I may start using that instead though.

---

### Post by argie on 2007-02-15
There's also IDLE if you've gotten used to seeing that name around but I think gedit offers decent syntax highlighting too.

---

### Post by Bloch on 2007-02-15
I am learning Python more or less for fun, though I hope to be able to help make some useful data collection scripts for my girlfriend's PhD in linguistics.

I use gedit with several tabs open, one terminal open in the folder with my python scripts and another running a python shell > so I can test snippets of code.

 Soon I will start to learn the GUI capabilities of wxpython.

I'm also at level 15 of the Python Challenge - it's a tough puzzles involving 50% python skills and 50% a devious mind. It's a greatr way to learn python.

---

### Post by dannyboy79 on 2007-02-15
could you point me in the right direction for trying out the python challange, if it open to the public that is? thank you

---

### Post by dannyboy79 on 2007-02-15
> **steve.horsley said:**
> I've been coding in python for a couple of years, just using the gedit text editor. I haven't had to write a python GUI yet, though. If you want to do that, I have heard good things about glade - google for it. Python is included in the default Ubuntu install - lots of the utilities use python.

I recently had a quick look at an editor called geany (there is an Ubuntu package for it) and I may start using that instead though.

if you're using dapper than python does not come installed by default. at least I had to install it. also, when you do a sudo aptitude show python, it states:
Package: python
State: installed
**Automatically installed: no**
Version: 2.4.2-0ubuntu3
Priority: important
Section: python
Maintainer: Matthias Klose <doko@debian.org>
Uncompressed Size: 545k
Depends: python2.4 (>= 2.4.2), python-minimal

which means just what it says. I just did sudo aptitude install python2.4 and I was set. here is a great place to learn, this is where I am trying to learn it, it has JavaScript and VBScript also, why those languages? Well, for a start they have very different styles to Python so you can form a useful contrast, and more prosaically if we accept that most Web surfers who are also beginners are using PCs with Microsoft Windows installed, there is a programming environment built in to the operating system called Windows Scripting Host which has support for VBScript and JScript (which is Microsoft's variant of JavaScript). good luck

[http://www.freenetpages.co.uk/hp/alan.gauld/](http://www.freenetpages.co.uk/hp/alan.gauld/)

---

