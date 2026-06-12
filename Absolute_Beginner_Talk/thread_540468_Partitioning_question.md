---
title: "Partitioning question"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Habitz on 2007-09-01
I'm a total newbie Ubuntu user and I'm a little worried about running out of space on my filesystem ext3 partition /dev/sda3. Right now I'm down to around 600 megs free space. I guess my question is, can I re-size this partition?  I have 4 gigs or ntfs partition that is basically sitting idle and unused.  Can I format this partition to re-size /dev/sda3 filesystem ext3? Thanks in advance.

---

### Post by bone2006 on 2007-09-01
Go here gparted.sourceforge.net/  and download gparted liveCD.  It's a linux liveCD partitioning utlity, and it can repartition your HD, it can perform a non-destructive partition.

---

### Post by Habitz on 2007-09-01
> **bone2006 said:**
> Go here gparted.sourceforge.net/  and download gparted liveCD.  It's a linux liveCD partitioning utlity, and it can repartition your HD, it can perform a non-destructive partition.

I have Gparted installed already. Can I use that to format my unused partition? Also, is it possible to re-size my existing /dev/sda3 partition?

---

### Post by southernman on 2007-09-01
You'll need the live cd to do your resizing as you can't do this to a mounted partition. You could download and burn a superb tool called SystemRescueCD, it has gparted on it along with other various tools. It's a great cd to have in your toolbox for most any emergency.

It also has a gui but doesn't start by default. When the cd drops you to the command prompt just type "startx" and you're set to go.

---

### Post by public_void on 2007-09-01
Boot from the liveCD as gparted won't resize a partition unless its unmounted. Booting from the liveCD will allow you to resize all you partitions.

---

