---
title: "Recover files on a window machine"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Hamm on 2007-02-08
I have a windows machine I need to recover some document files from before I put Ubuntu on it. They are all MS Office files. Any ideas?

Hamm

---

### Post by tribble222 on 2007-02-08
Do you mean that you suffered a hard disk failure and need to recover files?  Is your windows hard drive fat32 or ntfs?

If the hard drive works, and you just want to grab some files off of it, but for some reason you can't boot windows, you could use an Ubuntu live CD to copy the necessary files to a floppy or burn to a CD or transfer across the network or to an external hard drive, etc.

---

### Post by Hamm on 2007-02-08
Please forgive me for being a n00b, but how do I do that with a ubuntu live CD? It is a XP pro that went bad (no surprise). I have a Live CD in it now. I just don't know how to access the window files.  :confused:

---

### Post by SoloSalsa on 2007-02-08
Are you using 6.06 or 6.10?

---

### Post by Hamm on 2007-02-08
6.10

---

### Post by SoloSalsa on 2007-02-08
okay...  I had to read up on this...  It would be much easier in 6.06, because they included a gui utility to mount disks.  6.10 removed it, so there is a bit of handwork to be done.  You can read Aysiu's article [here]("http://www.psychocats.net/ubuntu/mountwindows"), or I'll step-by-step it to you.
open a terminal; post the output:
> code: sudo fdisk -l

---

### Post by letitsnow on 2007-02-08
i like knoppix for this because it automatically mounts the partitions. i like ubuntu better for just about everything else though.

---

