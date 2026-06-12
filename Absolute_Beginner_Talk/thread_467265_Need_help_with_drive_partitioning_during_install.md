---
title: "Need help with drive partitioning during install"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by diablo75 on 2007-06-07
I'm trying to install Ubuntu on a DV9000 and I'm running into a problem with the partitioning tool.  I am wanting to do a dual boot setup.  Currently (according to Computer Management>Storage in windows control panel) there are three hard drive partitions shown:

1. A 1.00 gig partition that has no name, but says that it's NTFS.  It has no drive letter.
2. The system partition, C:
3. An 11.49 gig partition, HP_Recovery, drive letter is D:

When I run the live CD,  gparted doesn't know what partition to select to resize.  And I don't know how to make my way around the Manual gparted controls, but I am wanting to resize the 2. (System) partition, and install Linux on it's own partition.

Can this be done without deleting any of these other partitions?  I just want to resize the C:.

---

### Post by locke.dragon on 2007-06-07
could you post a screenshot of how gparted looks in the live cd?

---

### Post by Espionage724 on 2007-06-07
You should be able to resize C: I did it once before when I had Windows XP. I couldn't do it with Vista for some reason.

---

### Post by diablo75 on 2007-06-07
I just realized that I wasn't actually looking at g-parted but instead the partitioning tool in the install dialog.  I found g-parted.  It wouldn't let me resize the partition because it asked me to scan the drive and check for errors, so that's what I'm doing right now.

We'll give it another try after scan disk is done doing its thing.

---

### Post by locke.dragon on 2007-06-07
make sure you defragment the drive before you try to resize it.  if you don't, you could possibly get some errors.

---

