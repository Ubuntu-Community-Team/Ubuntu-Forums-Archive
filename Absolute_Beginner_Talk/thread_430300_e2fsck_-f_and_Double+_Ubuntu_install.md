---
title: "e2fsck -f and Double+ Ubuntu install"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by jaredssix on 2007-05-02
Hey all,
it appears that I have Ubuntu double installed (or more). On my dual boot start up, I can select from 4 (!) Ubuntus and 1 Windows. 

Long story short, I started recently with 6.10, and the partitioning features proved scary. So I then loaded up 6.06, and have upgraded to 6.10, and now 7.04.

I'm running into space issues, and it has been suggested that I run e2fsck -f on my mounted partition. This also scares me, as the command line threatens potential severe damage to the drive. 

What should I do? Expand my used partition over the others, perhaps via 7.04 LiveCD? How can I erase the others? I'm not worried about losing anything, really, except for my Windows partition (which I need for AutoCad, MathCad, ArcGIS, etc.)

Thanks in advance!

---

### Post by mikeyphi on 2007-05-02
It is normal to have 2 Ubuntu options plus 2 recovery options.....if you have a problem with the newest load you can boot into the older version and sort things out!!

To reclaim disk space - open a terminal and enter:

sudo apt-get clean

this will get rid of all the old packages you downloaded but will not touch the current system.

---

