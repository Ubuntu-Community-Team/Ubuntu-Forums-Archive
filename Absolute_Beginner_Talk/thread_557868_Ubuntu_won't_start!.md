---
title: "Ubuntu won't start?!"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by aheicher on 2007-09-23
Dell Dimension 3000, Ubuntu Desktop 7.0.4
Running Ubuntu off of an external 80GB hard drive, have windows Dual-Booting from my main
Everytime I try to start Ubuntu, it logs in as a terminal login and it won't take me to my login screen.  It says drive image not found in /dev.
I could use some help
what I was doing before I did this was installing XGL and Beryl
I edited the following files
/etc/X11/xorg.conf
/usr/share/xsessions/xgl.desktop
/usr/bin/startxgl
i believe its a graphics problem, PLEASE HELP!!!

---

### Post by banewman on 2007-09-23
As a first guess when you edited xsessions did you list your external drive as /dev/something instead of what ubuntu calls it - hdb1 or something similar ?

---

### Post by juantovarm on 2007-09-23
Didi you make a backup of the old files? I can only help you with the xorg.conf

you edited your xorg.conf.....
try reconfiguring it:
type and follow the commands:
sudo dpkg-reconfigure -phigh xserver-xorg

Hope it helps

Juan

---

### Post by HokeyFry on 2007-09-23
did you back up your original files? if you did try restoring them to their original state and see if tht fixes anything

---

### Post by aheicher on 2007-09-23
i fixed it, it was the xsessions file-
I still cant get XGL and BERYL to work the way they're supposed to though, any help on that would be appreciated
I have and intel i8xx graphics card

---

### Post by overdrank on 2007-09-23
> **aheicher said:**
> i fixed it, it was the xsessions file-
I still cant get XGL and BERYL to work the way they're supposed to though, any help on that would be appreciated
I have and intel i8xx graphics card

Hey I have never tried xgl and intel. Might have to investigate. Why did you decide to try xgl and intel it works great on my laptop with out the xgl sessions?

---

### Post by aheicher on 2007-09-23
half the stuff on beryl never worked, and now none of it works
the flame thing, all the other effects just stopped working
and I did xgl, its slow as crap and dosent work, should i reinstall beryl?

---

### Post by overdrank on 2007-09-23
> **aheicher said:**
> half the stuff on beryl never worked, and now none of it works
the flame thing, all the other effects just stopped working
and I did xgl, its slow as crap and dosent work, should i reinstall beryl?

Yes I would start there and how much memory does your system have?

---

### Post by aheicher on 2007-09-23
im using 80GB external HD, 512 MB ram

---

### Post by aheicher on 2007-09-23
ill be back in two hours, please post help tips, thanks guys

---

### Post by overdrank on 2007-09-23
> **aheicher said:**
> ill be back in two hours, please post help tips, thanks guys

THe only thing I can think of is it being on a external drive may cause problems.

---

