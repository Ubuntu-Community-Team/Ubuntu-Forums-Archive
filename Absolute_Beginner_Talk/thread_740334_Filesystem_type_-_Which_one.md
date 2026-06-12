---
title: "Filesystem type - Which one?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by Executioner on 2008-03-30
Hi everyone,
I have successfully installed Ubuntu 7.10 on a SCSI HD as boot. I also have 2 120gig IDE drives that I ran Boot & Nuke on to wipe them completely before the installation of Ubuntu. I want to be able to use these 2 IDE drives for data storage. When creating a new partition, I have several options for the file system type:
ext2
ext3
fat16
fat32
linux-swap
reiserfs
unformatted
What are the differences between ext3 and ext2? Are there any advantages in using ext2 or 3 over fat32?

---

### Post by StOoZ on 2008-03-30
the standard recommendation is ext3.
but it depends on what your aims for that system.

---

### Post by annda on 2008-03-30
i believe that for most users the differences between ext2 and ext3 are not important. however, compared to fat32 you get less disk fragmentation (some will say: none) and you can/have to manage user access rights.

---

### Post by markharding557 on 2008-03-30
ext3 is a journaling version of ext2 and these are better than fat because they have much less defragmentation,ext3 is the most commonly used fs in linux

---

### Post by Executioner on 2008-03-30
OK thanks everyone. I'll select ext3.

---

### Post by smurphy_it on 2008-03-30
ext3 is the most common.  Reiser usually handles big files better.  So if you were running a file server with alot of big files on them (say ISO's for example) you might be better off going with reiser.  Otherwise, I'd choose ext3.

---

