---
title: "Help!  About to abandon Ubuntu!  Installation problem!"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by getmeoutofhere on 2007-11-22
Gutsy doesn't work for me.  I need to install 7.04 on my Inspiron 1520 or I'm going to give up on Linux.

7.04 Alternate disk doesn't work.

Mini disk doesn't work.

Live CD gives this error:

/bin.sh: can't access tty; job control turned off (initramfs).

Looked on Google, but the suggested solutions don't work.

Any suggestions?  I need my computer very soon, and it looks as if I'll no option but to use Vista from now on.

Thanks in advance.

---

### Post by Dr Small on 2007-11-22
If every cd you burn is giving you problems, you must diagnose where the problem is coming from.

A.) You are burning them at to fast a speed
B.) Your Writer isn't working properly
C.) Your ROM needs cleaned
D.) Your ROM is going bad.
E.) Something wrong with your hardware

---

### Post by taurus on 2007-11-22
Did you remember to check the integrity of the ISO image after you've downloaded it, before you burnt it?  Then, make sure you burn it at a slow speed like 4x if possible.  And after you boot from the CD, pick the option from the menu to check the CD to be sure everything on it is good before you run or install from it.

---

### Post by fenixphire07 on 2007-11-22
Hey, i remember having a similar problem with 7.04 when i first got it. The best option maybe to use Windows 98 2nd edition cd and boot into ms-dos. then delete all your partitions and dont create any new ones. exit fdisk utility

Then place the live cd in your cd rom and restart. 

oh, i believe it actually a problem with ur master boot record. i have seen a command called fdisk \mbr - google it or even better ubuntuforum it.

Good luck men, hope you can kick windows

---

### Post by Sef on 2007-11-22
> Any suggestions? I need my computer very soon, and it looks as if I'll no option but to use Vista from now on.

Or you could try another GNU/Linux.   Sometimes one version will work where others wont'.

---

### Post by Dr Small on 2007-11-22
> **Sef said:**
> Or you could try another GNU/Linux.   Sometimes one version will work where others wont'.
Right on. I have a Fedora CD and for some reason it won't boot with this machine but it would for the other one... Go figure.

---

### Post by Wiebelhaus on 2007-11-22
Sounds like a hardware issues , I'd be interested to hear how successful a windows installation goes ,if you could tell us the exact error then we would be able to help otherwise , good luck.

---

### Post by getmeoutofhere on 2007-11-22
The CD is fine.  I've used it to successfully load Feisty on two other machines.  Managed to load Gutsy via the alternate CD on the Inspiron, but not via the live CD.

---

### Post by JBAlaska on 2007-11-22
I had similar (but not exactly the same) problem on dell and HP machines, the solution was to add ```
all_generic_ide
``` to the boot options. (F6 at the initial screen).

You can also try using the "Boot with Driver CD" option and leave the LiveCD in the drive and hit enter twice when prompted,

---

### Post by getmeoutofhere on 2007-11-22
JBAlaska,

Thanks for the suggestions.  

The Driver Update option creates the same problem.

The F6 possibility creates the same problem as I get with the 7.04 alternate disk.

I get a message that says something like

'Failed to start the X server (your graphic interface).  It is likely that it is not set up correctly.'  

The screen is blue.

---

### Post by polhen on 2007-11-23
hi...

i had the same problem, but i changed installation to ide drive instead of raid controller
to install ubuntu 7.04 you have to have ext.partition on the ide drive not raid controller

regrads
pol

---

