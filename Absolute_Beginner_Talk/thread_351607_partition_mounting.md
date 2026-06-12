---
title: "partition mounting?"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Big_Croc7 on 2007-02-02
Hi,
I'm having a weird problem since trying to install Windows XP (have happily been running Ubuntu alone for a while, but I needed to run some windows programs and decided that was the best way to do it).  However, trying to install it has messed up my Ubuntu install.

Until two days ago, my system was setup with separate partitions for root, swap, boot, grub, home (mostly xfs) and a fat32 data partition (with plenty of free unpartitioned space).  After spending an evening trying, and failing, to install WinXP (twice! but that's a different problem :(  ) I binned it and went back to just Ubuntu.  It's all fine, except that for some reason my home partition is no longer mounted.  I didn't touch any of the Ubuntu partitions except for shrinking the boot partition slightly; everything else works fine but now I have a /home directory on the root partition.

Any idea why this has happened??? XP wrote to the MBR, but then I installed grub back to it and everything else works fine - except I couldn't log in to gnome till I figured out what permissions /home/user needed :o  I guess I need to somehow automount it but have no idea why anything has changed in the first place. :confused:

---

