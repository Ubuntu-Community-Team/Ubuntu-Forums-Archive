---
title: "question about mount points"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by apathos on 2007-01-09
I'm trying to install Edgy Eft to make a dual boot situation.  I have 2 physical hard drives, and I'm trying to install onto the second drive (60 GB).  I have repartitioned to have the first half (of the second HDD) as FAT32 (for backup for the first HDD).  Then I have 3 partitions in the second half--1 for /home, 1 for '/'. and one for swap.  All are ext3.

The question I have is when I get to step 6 (mounting points in Gparted), it shows me the 2 partitions on the first HDD as well, and has them put in as /media/hda1 and /media/hda5, respectively.

Is this normal?  I know nothing about how mounting points work, so I want to make sure I'm not going to mess up anything as I do this.  I've tried just leaving them blank, but it doesn't let me do that.

Help!

---

### Post by sardion on 2007-01-09
As long as they are mounting in /media/XXX and the checkbox for formatting is *not* checked, you are good to go.  Those partitions will be left alone during the install.

---

