---
title: "Installing from source"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by bobbyshafter on 2007-02-27
I downloaded tunapie ,extracted in my home dir.
 I then cd to my home dir ,execute ./configure....... get a message not in this dir.
 I then look at the install read-me ..

Install tunapie with:
sh install.sh

or, for full non-censored tv listings, 

sh install.sh --adult

Uninstall with:

sh uninstall.sh

I the tried to compile with make .....file does not exsist.

I think you woul have to compile before running the install script..

What am i doing wrong...

I HAVE ALL THE TOOLS INSTALLED..

This my 2nd packadge i am compiling...help

---

### Post by aysiu on 2007-02-27
I'm not sure if this'll give you weird dependency problems, but you could try installing the Feisty package: ```
wget -c http://mirrors.kernel.org/ubuntu/pool/universe/t/tunapie/tunapie_1.3.1-1_i386.deb
sudo dpkg -i tunapie_1.3.1-1_i386.deb
```

---

### Post by lunadog on 2007-04-03
> **bobbyshafter said:**
> I think you woul have to compile before running the install script..


Not in this case. It is written in Python.

---

### Post by dannyboy79 on 2007-04-03
when the install instructions tell you what to do, then that's what you do. I am not trying to be rude here but the developers write up install instructions for a reason. so yes, all you have to do to install it is run the python install script.

---

### Post by bobbyshafter on 2007-04-03
Dannyboy i did follow the read me first with no luck.

---

### Post by ComplexNumber on 2007-04-03
**bobbyshafter**
a few options come to mind.
-you need to run it as root. therefore, you need to go to the direcory as before and type in the following:
[B]sudo ./install.sh
[/B]strangely, it doesn't say that in the instructions when it should do.

further problems may be due to the fact that python-wxgtk2.6 is need to run it, so this needs to be installed. it says that some of the python-Egenix packages need to be installed.

---

### Post by dannyboy79 on 2007-04-04
> **bobbyshafter said:**
> Dannyboy i did follow the read me first with no luck.

i apologize than, you made it sound like you never tried that and that all you tried was ./configure and it wasn't working and you didn't go any further because you thought you needed to compile before running the script. do you have python from the repo's installed? maybe even python-dev packages if it's not working? also, if you open the python script itself, where does it say it's looking for python? it may be something like #!/usr/bin/python. make sure that's where you have python installed if not, you can change it to where ever you installed python. or you can make a symllink (the better solution so future scripts don't fail also) to the real location and put it in /usr/bin/.

---

### Post by lunadog on 2007-04-04
> **ComplexNumber said:**
> **bobbyshafter**
a few options come to mind.
-you need to run it as root. therefore, you need to go to the direcory as before and type in the following:
[B]sudo ./install.sh
[/B]strangely, it doesn't say that in the instructions when it should do.

Oops! My mistake.. Yes it should be installed as root.

> further problems may be due to the fact that python-wxgtk2.6 is need to run it, so this needs to be installed. it says that some of the python-Egenix packages need to be installed.

Not anymore. just python wxgtk2.6

I would really advise using the ubuntu or debian packages rather than building from source though.. seeing as I went to the bother to build the packages (well at least the Debian ones!).

---

