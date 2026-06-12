---
title: "A way to bring up the login screen from the terminal"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by unixnorks on 2006-01-28
Hi guys and to all the ubuntu guru outthere!

First of all im an avid ubuntu user though still a newby... Im working on a school preferrably a php/java programmer. The school uses Ubuntu as their main OS. Each workstation is being centralized through a NIS.

My question is how to bring up the login screen by issueing some command to the console...

i know this command ====> /etc/init.d/gdm restart but just falls me to the black screen called console or tty...

Any ideas?

Thanks in anticipation of your being cooperative..

---

### Post by bscbrit on 2006-01-28
Is X running?  Try

startx

or

sudo startx

on the commandline.  Not sure if this is the solution though....

---

