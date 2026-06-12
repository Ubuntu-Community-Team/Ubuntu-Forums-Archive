---
title: "slave hard drive locked!"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by gimpy04 on 2007-08-03
I have this lovely 120 gig western digital hard drive That was given to me at work by  a customer!! and it seems to be locked so i cant format it how do i unlock this thing!
please help
dustin

:guitar:

---

### Post by Alterax on 2007-08-03
If it's "Locked", it's probably mounted as an NTFS Read-only drive.

First, find out if it has any partitions mounted:

df -a

Unmount the partitions:

sudo umount /dev/hdb1 
 (this is assuming the drive is  /dev/hdb with just a partition1 on it.  Modify as needed.)

then run qtparted.  It's a tad easier than doing it all through the terminal window:

sudo qtparted

---

