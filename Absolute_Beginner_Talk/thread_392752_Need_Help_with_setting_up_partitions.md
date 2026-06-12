---
title: "Need Help with setting up partitions"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by chymo on 2007-03-24
I'm reinstalling ubuntu 6.06 to an 80GB hard drive.  I've had issues with gdm crashing and believe it is due to ext3.  Do you have a recommended approach to creating partitions on installation?

---

### Post by martinw89 on 2007-03-24
When reinstalling an OS, I personally delete the old partitions related to it and then select to use the largest continuous free space when installing.

Why do you think Gnome Display Manager problems were related to ext3?  Are you saying you would like to install Ubuntu on something other than ext3?

---

### Post by chymo on 2007-03-24
So if I do "largest continuous space" will this erase all other partitions?  

I have used Ubuntu on two Dells, both have issues with gdm locking up sporadically, although you can still ssh into the box.  It is a weird issue but both were basic installs.  

I've heard that reiserfs is a popular option.  What should I use for root and swap?  I have basic needs as this is mostly a LAMP installation.

---

### Post by martinw89 on 2007-03-24
Largest continuous space is non-intrusive and won't change any of your partitions. Swap space has it's own partition type, for root that's up to you.  I've never used reiserfs before but I'm sure you can find plenty of information on using it.  I still think it's odd that ext3 would cause GDM to lock up, that would more typically be something caused by display drivers.

-Martin

---

