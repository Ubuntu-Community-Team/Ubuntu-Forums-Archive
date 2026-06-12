---
title: "Xserver gdm problem on install"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Coldfrontt on 2007-03-19
Hi everyone. I'm a real beginner at this (the only thing I know for sure is that penguins seem to like linux).
trying to install Ubuntu or even start a live session, I get a problem where xserver seems to develop a problem apparently detecting either my vid card, or monitor. the only thing I can decipher is screen=0, which I assume is some kind of video config error. I'm using a 8800GTX card and am wondering if it is too new for 6.10 to recognize. Shouldn't the install default to a "safe" basic VGA driver?
The process ends at a prompt:
Ubuntu@ubuntu
I'm clueless what to do. The same thing happens with Kubuntu.
Mandrivia installs, but does not recognize the card, which I'm assuming is also a driver issue.
Thanks in advance

---

### Post by zvacet on 2007-03-19
ctrl+alt+F1 will bring you to terminal
```
sudo dpkg-reconfigure xserver-xorg
```
pick **vesa** driver

---

### Post by Coldfrontt on 2007-03-19
People here are gonna get very tired of me.
After that, it warns me to back up the config, but since there is no file yet to write to (I think), that is probably not a problem.
How do I continue the install after making the changes?
It drops me back to the ubuntu prompt, and I'll be damned if I can figure out what comes next. tried the start gmd command but it says I have to be the root. There is no root account at this point, is there?

---

### Post by Coldfrontt on 2007-03-19
Found the solution... sudo dpkg-reconfigure gdm.
At least now live session runs.

---

