---
title: "wine install problem"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by jbumgar on 2006-09-10
I got this message when when I typed in wine cfg:

jim@jim-desktop:~$ wine cfg
wine: creating configuration directory '/home/jim/.wine'...
wine: '/home/jim/.wine' created successfully.
wine: could not load L"c:\\windows\\system32\\cfg.exe": Module not found
jim@jim-desktop:~$

I'm guessing it didn't install correctly. Has anyone else had this problem and fix it?

---

### Post by meng on 2006-09-10
It's not wine cfg
it's winecfg

---

### Post by jbumgar on 2006-09-10
Sorry about the typo I did type winecfg the first time.

---

### Post by meng on 2006-09-10
Really? Because the screen output you posted is consistent with what you would get if you typed:
wine cfg

What is the error output with
winecfg

---

### Post by baylorbear on 2006-09-10
Wine Tools is easier to use anyhow...
[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

---

### Post by jbumgar on 2006-09-10
It brings up the wine configuration panel. But it doesn't work when I try to add my games or apps. It just shows program files which only has common in it

It shows the windows folder which has a few things in it system32 folder and a few files in it.

---

### Post by meng on 2006-09-10
AFAIK, you're not supposed to use it to install/add programs. To do that, change to the directory where you downloaded the program, and type:
wine setup.exe (or install.exe or whatever)

---

