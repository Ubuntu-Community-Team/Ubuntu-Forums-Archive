---
title: "Well.. Ubuntu is easier than I thought, but 1 simple question"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Zaosyn on 2007-04-22
Well I started out Ubuntu 2 days ago. From installing 6.06, and upgrading to 6.10, and then upgrading again to 7.04

My personal experience with Linux was only Mandriva and it was a pain.. With Ubuntu it literally feels 100x easier installing items, and what not. I **love** it. However I'm still depending on Windows for a few things, which I would like to eventually leave and become a 100% Ubuntu user. 

My question is, on my hard drive that is partitioned into 2 drives, a windows drive ( 120 gigs ) and my Linux partition ( 30 gigs ). I would like to take all my music,videos,pictures off my WIndows partition and move them to my LInux one.

I noticed when I Start windows and go to C: I only see my Windows partition and not my LInux.. My original plan was to just copy everything from my WIndows partition I Wanted and just move it in a folder on my Linux, using XP to do all of this, but since Linux partition doesn't show up, I'm lost on how I Would go about moving items.

If you could please tell me how I Would go about moving files from my Windows partition onto my LInux one I would be very greatful.

I'm 1 step closer to making the final step and going completely Ubuntu.

---

### Post by Michaelt74 on 2007-04-22
Windows doesn't allow read access to the Linux partition. When you boot Ubuntu your Windows partition (Hda1) should appear on your desktop. From there you can access the Windows files and copy and paste them to your Linux partition. This may help:

Check the part about mounting Windows

[http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/](http://opensourceroolz.wordpress.com/2007/04/20/a-quick-customisation-setup-guide-for-ubuntu-feisty-704/)

---

### Post by Zaosyn on 2007-04-22
HOLY CRAP! All this time I thought HDA1 was just my Linux partition onto my desktop. But it's really my WHOLE hardrdrive including WIndows. I can see all my files.. Thanks for making it more simple for me.

---

### Post by tgalati4 on 2007-04-22
Many users are in this situation.  There is no easy solution but several workable ones.

As drives are cheap these days, Buy another one, Format one large partition as FAT32 and put all your media on it.  Then Windows or Ubuntu can get access to it.
Put a small swap partition on it so that you can test future Live Distros that run better with an external swap partition.  Put a small (4-6 GB) partition as Ext2 or Ext3 so that you can put a future Linux install (say Gutsy Gerbil) or to use as a backup Linux boot drive incase your current install takes a dump.

If you don't have room for an internal drive, a USB external drive may work as well.

I assume this is not a laptop based on the size of the drive.

Good luck.

---

