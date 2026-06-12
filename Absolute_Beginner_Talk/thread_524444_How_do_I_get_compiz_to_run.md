---
title: "How do I get compiz to run"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by avanrens on 2007-08-13
I have installed Ubuntu ultimate and have found CompizConfig Settings in System> Preferences> But how do I get Compiz to run.

---

### Post by jambarama on 2007-08-13
> **avanrens said:**
> I have installed Ubuntu ultimate and have found CompizConfig Settings in System> Preferences> But how do I get Compiz to run.

The first thing I can recommend is the [the Compiz section in the Ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Compiz_.2F_Desktop_Effects").  The people who wrote this guide are a lot smarter than I am.  Anyhow, on to my advice.  

I'm going to assume you have Compiz installed, I guess it is part of Ubuntu Ultimate.  Has Ubuntu detected & loaded the drivers for your video card properly?  If you aren't sure, open a terminal and type the following: > modprobe -l | less  Look for something like aiglrx/flgrx (if you have an ati card) or nvidia-glx (if you have an nvida card).  

If you know which card you have, and you know the driver is installed, you may want to run through and reconfigure X with this command: > sudo dpkg-reconfigure xserver-xorg  For most options just go with default, but when asking you about modules make sure you add the "glx" module.

---

### Post by avanrens on 2007-08-14
Worked it out Just type compiz --repace to run Compiz, Great program. Any on no where the documentation is stored?

---

