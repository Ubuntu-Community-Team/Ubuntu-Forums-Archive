---
title: "Is this the right place for Kubuntu newbies?"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by eric.stone on 2005-09-15
Hi. I'm trying to install Quantaplus.  When I run configure I get:

configure: error: no acceptable C compiler found in $PATH

Can anyone help?

Thanks,
Eric ](*,)

---

### Post by numberexhaust on 2005-09-15
[QUOTE=eric.stone]Hi. I'm trying to install Quantaplus.  When I run configure I get:

configure: error: no acceptable C compiler found in $PATH

Can anyone help?

Thanks,
Eric ](*,)[/QUOTE]
 sudo apt-get install build-essential

---

### Post by dave9191 on 2005-09-15
You are trying to compile Quanta Plus, however you have no tools to compile it with on your computer. You need to install a bunch of libaries and a compiler and anything else that configure would complain about before it will let you continue to the next step. 

However, there is an easier way to install it rather then compiling it. Add extra repositories as described in ubuntuguide.org. Note that when it says gedit, you want to put kedit or kate. Gedit is a gnome text editor you wont have intsalled if you have KDE (as in kubuntu). 

Then you can install it by typing 

sudo apt-get install quanta

That will download and install all the files you need. I'm assuming you have a working internet connection on that machine :)

Dave

---

### Post by eric.stone on 2005-09-15
[QUOTE=dave9191]You are trying to compile Quanta Plus, however you have no tools to compile it with on your computer. You need to install a bunch of libaries and a compiler and anything else that configure would complain about before it will let you continue to the next step. 

However, there is an easier way to install it rather then compiling it. Add extra repositories as described in ubuntuguide.org. Note that when it says gedit, you want to put kedit or kate. Gedit is a gnome text editor you wont have intsalled if you have KDE (as in kubuntu). 

Then you can install it by typing 

sudo apt-get install quanta

That will download and install all the files you need. I'm assuming you have a working internet connection on that machine :)

Dave[/QUOTE]
 Thanks, Dave.  I'm learning to fish!

---

### Post by eric.stone on 2005-09-15
[QUOTE=numberexhaust]sudo apt-get install build-essential[/QUOTE]
 Thanks!!!  I'm off to try it. :smile:

---

### Post by eric.stone on 2005-09-15
[QUOTE=dave9191]You are trying to compile Quanta Plus, however you have no tools to compile it with on your computer. You need to install a bunch of libaries and a compiler and anything else that configure would complain about before it will let you continue to the next step. 

However, there is an easier way to install it rather then compiling it. Add extra repositories as described in ubuntuguide.org. Note that when it says gedit, you want to put kedit or kate. Gedit is a gnome text editor you wont have intsalled if you have KDE (as in kubuntu). 

Then you can install it by typing 

sudo apt-get install quanta

That will download and install all the files you need. I'm assuming you have a working internet connection on that machine :)

Dave[/QUOTE]
 Worked perfectly.  Quanta is up & running.  Got a message about needing several files for full functionality.  Do I just apt-get them the same way?

---

### Post by dave9191 on 2005-09-16
Hey, glad you got it running :) You can try and get them the same way. As long as you have the name of the package you can install stuff this way. Some things have a different name to their package. Like Quanta Plus has quanta instead of something like quanta_plus. 

You can also use Kynaptic ( in the menu ) to install things using a graphical method. I would recommend that you install Kpackage or synaptic and use one of them instead of kynaptic tho. They allow you to tick the programs you want to install and click apply. This way you can also browse the programs in the repositories that you can install without have to get an install file or the source code youself.

---

### Post by eric.stone on 2005-09-16
Thanks again.  I'm going to hunt down those extra programs tomorrow.

---

