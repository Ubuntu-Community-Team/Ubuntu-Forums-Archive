---
title: "ready to say goodbye . . ."
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by matthewstory on 2005-12-07
. . . to windows xp, and i'm looking to wipe the windows partition and reformat it and make it part of my Ubuntu partion.  I have two questions:

1. is there an easy way to do this?

2. is it possible to just add the space to my ubuntu partition, and thereby make the whole disc one big happy unit?  Or will i have to make it a seperate partition that ubuntu has read/write access to?  If this is the case, should i still format it ext3, or should i give a different format a try?

thanks all

matt

---

### Post by aysiu on 2005-12-07
Theoretically, [GParted](http://gparted.sourceforge.net/screens/gparted_4_big.jpg) or [QTParted](http://www.linuxsoft.cz/screenshot_img/970-a.jpg) can do this for you--delete the Windows partition and expand your current partition to fill the empty space. However:

1. If you're making changes to your current partition (even expanding it), you'll need to back up everything *and* run GParted or QTParted from a live CD.

2. GParted and QTParted are fine as partitioning programs, but sometimes (for some unknown reason) they won't let you do certain things you're supposed to be able to do (the option is greyed out). I know it seems an extreme workaround, but I have a Mandriva installer disk (just the first one) handy all the time, because I've found its partitioner ([DiskDrake](http://iew3.technion.ac.il/CC/Comp_news/Mandrake_starter/images/diskdrake-main.png)) to be failsafe.

---

