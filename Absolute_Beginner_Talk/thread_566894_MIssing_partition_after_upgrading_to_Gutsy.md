---
title: "MIssing partition after upgrading to Gutsy"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by danburke on 2007-10-04
I just updated to Gutsy, and everything works fine for me, except a partition is missing. When I installed ubuntu I kept all the music and videos that were on the hard drive in their own partition. It showed up with Feisty, but now it doesn't.

---

### Post by dwhitney67 on 2007-10-04
Have you examined the /etc/fstab file on your system?  Perhaps there is an entry missing.  If you forgot the partition device (e.g. /dev/hda4), then run fdisk to examine the partitions on your HDD.

---

