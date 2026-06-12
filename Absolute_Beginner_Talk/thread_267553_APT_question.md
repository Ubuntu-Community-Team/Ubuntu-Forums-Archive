---
title: "APT question"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by neumeka on 2006-09-28
When I install a package using apt-get install or using synaptic, is there I way that I can tell which executables were installed?  This is often frusterating because after I install a package, I have to google the package to figure out the command to run the program, or figure out how to "man" it.

---

### Post by PPAAUULL on 2006-09-28
Usually it is the name. EX for a game called boson you type ```
boson
``` Try that first. It is usauly the best bet to try the name. I also think there is a program that will make start menu entries, because this is the same problem I have run into. I can't seem to remember the name of it. If anyone could tell us that would be great!!!

---

### Post by xpod on 2006-09-28
You can right click any package in synaptic and go into it`s properties to see all installed files and their locations i think.

As far as "apt-get" is concerned this seems to be generally the better choice

[http://psychocats.net/ubuntu/aptitude](http://psychocats.net/ubuntu/aptitude)

Not 100% sure where actual executables are

EDIT:if you just want to run an app you can type it`s name in the terminal
or if it`s not showing up in the menu try installing the debian menu which is great for showing all apps

---

### Post by llamakc on 2006-09-28
You can see each file installed by a package on the command line with:

dpkg -L nameofpackage

---

### Post by neumeka on 2006-09-28
Thanks.  The dpkg trick was what I was looking for.

---

