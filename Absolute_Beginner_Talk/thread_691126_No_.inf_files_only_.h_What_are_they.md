---
title: "No .inf files only .h? What are they?"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by JoJoArmani on 2008-02-08
Hello trying to find .inf .sys files/driver for my amtel chipset pcmcia card. 
I have downloaded the necessary files but I can't see a .inf or .sys file to load via ndiswrapper - most of the files are .h or .c. 

What do I need to do?

Thanks!

---

### Post by jasmuz on 2008-02-08
Those are header and compiler files, meaning you downloaded the source for the drivers not the drivers themselves.

---

### Post by stump138 on 2008-02-08
You have downloaded source code from somewhere.  .h and .c files are header and source code files written in the "C" programming language.  You are looking for a winxp driver download to use with ndiswrapper, and you probably got the driver's source files instead.  You'll want to look for a diff download :)

---

### Post by eggdeng on 2008-02-08
The easiest way to get hold of these is simply to copy them from your working XP installation, assuming of course, that  you have one.

---

