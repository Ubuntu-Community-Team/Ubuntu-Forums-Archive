---
title: "Fiesty Partitioning Help"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by wolfroolz on 2007-04-21
This might seem like a silly question, but I am so stuck.

I recently got a dell inspiron 1505.  120 Gig hd, 2 gigs of ram, 256 mb ati x1400  card, core2duo 1.83 ghz.

I reinstalled vista onto a 30 gig partition.  My hard drive is a follows, 

vista >30 gigs - primary
media direct >2 gigs - primary
eisa config >50 megs - primary
unallocated space > 80 gigs

When I try to install ubuntu from the main cd, I get an error, X server can not load.  Same error when I tried loading in safe graphical mode.  I went into the forums and found the post about installing with ati x cards.  I burned the alternative cd, and tried booting in text mode.  Everything seems to be going ok, until I get to the part about partitioning the drive. What I want ultimately is this

vista >30 gigs ntfs - primary
media direct >2 gigs - primary
eisa config >50 megs - primary
ubuntu > 20 gigs - ?
swap > 2 gigs
data > 58 gigs - fat32

So I go into manual and I create a 20 gig partition, select done editing this partition.  This takes me back to the list of my hd partitions and I see the new one there.  Now what?  When I go into guided partition I can not select that partition, and if I go and select the partition I made it just takes me back into editing that partition.  What am I missing?

---

### Post by jem7v on 2007-04-21
[http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm) might help you.

---

### Post by marx2k on 2007-04-25
I dont get why Ubuntu did away with GParted i their installer. That was the best program to use for manual installation, resizing partitions graphically, etc.

The partitioning scheme they have now is awful comparatively. Very annoying.

---

