---
title: "Ubuntu on Windows Machine, Et Cetera"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by lebesgue4234 on 2008-04-18
So, I have recently been introduced to Ubuntu because all of the mathematics department machines at my school use it, and I want to put it on my home PC, but I have virtually no clue how it will work. I currently have Windows XP; when I install Ubuntu, what will happen to XP? Will I still have all the applications I've installed with XP? I guess I just really have no idea what to expect, and I was wondering if I could get some information on that. Thanks a lot.

Keenan

---

### Post by Crafty Kisses on 2008-04-18
You could always partition, so you can have both Windows XP and Ubuntu, there is a great tutorial at [www.psychocats.net](www.psychocats.net), you might want to check it out. :)

---

### Post by bumanie on 2008-04-18
What I would do is download gparted live cd ([here]("http://gparted.sourceforge.net/")) and first shrink your windows partition with that and then format the unallocated area to ext3. During the installation process, you are given the choice of how to partition your hard drive (the installation has its own partitioning program). Choose manual and click on the unallocated patition and choose edit. Make a 7-8g / a 1-2 g swap (both are mandatory) and then make a separate /home. This way if something goes wrong with the filesystem, your saved data will be sfae in /home and you will only have to reinstall to /.

---

### Post by erginemr on 2008-04-18
Here are two step-by-step guides on graphical installation from the Ubuntu Live CD:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://mbalat.blogspot.com/2007/11/ubuntu-710-installation-walkthrough.html](http://mbalat.blogspot.com/2007/11/ubuntu-710-installation-walkthrough.html)

You should be extra careful not to wipe off your Windows partition during the install.

You may also consider waiting for one week when Hardy Heron, the new version of Ubuntu will be released, which will have an option to install Ubuntu as if it is just another Windows software, without partitioning your hard drive, via a software called Wubi. Yet, I would suggest you to take the plunge, partition your hard drive and do a real installation.

---

### Post by noswal on 2008-04-18
Installing a second hard drive is also an option, second hand ones are not too expensive.

---

### Post by louieb on 2008-04-18
> **lebesgue4234 said:**
> ... what will happen to XP?...have no idea what to expect...

:) Options its all about options. Depending on how you install Ubuntu Linux you can dual boot your PC and choose to run XP or Ubuntu.  You can wipe XP  it programs and all your data off and start out fresh with Ubuntu.  You can run XP inside Ubuntu or Ubuntu inside XP  (virtual machine). 

Dual booting is the most common way a new Linux user sets up their PC.
See the Installing Ubuntu sticky in the Absolute Beginner section. 

Its not hard but you do need to be careful (backup). I suggest you invest in a 2nd hard drive.   Heres a good thread on dual booting Linux and windows  on two hard drives.  [Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

---

