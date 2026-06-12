---
title: "Can't have the end before the start! ERROR."
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2007-11-25
I get this error when installing Ubuntu 7.04.

"Can't have the end before the start!"

I have the following partitions...

/ 20gb ext3
swap 1gb swap
/home rest of hdd, this is where the error comes up

This is a 250gb hdd, and I can't understand why I've been able to make this EXACT same partition scheme long ago and not now.  What's going on?

---

### Post by zetsumei on 2007-11-25
anyone?

---

### Post by kajillin on 2007-12-04
I have this same problem

Can't have the end before the start! ????

Dont know what to do?

im trying to partition my 300Gb maxtor
Running fiesty fawn
tried writing at the begining and the end, same result
Someone please respond

---

### Post by hyper_ch on 2007-12-04
do the partitioning before you start installing and then use the manual partitioning option during the install process.

---

### Post by kajillin on 2007-12-04
It wont let me partition the disk period.... it tells me "error while setting new disk label" in the gnome disk partitioner
is there any other way i can format the drive through ubuntu?

---

### Post by hyper_ch on 2007-12-04
is the disk already mounted when you try to partition it?

---

### Post by kajillin on 2007-12-04
when i try to mount it i get this error

"mount:/dev/sda1 is not a valid block device"

---

### Post by hyper_ch on 2007-12-04
is any of those partitions on that disk already mounted when you try to partition it?

---

### Post by kajillin on 2007-12-04
well i can see the drive, it is all unallocated space, it did that during the installation process. so no the disk is/and was setup as a single partition.

---

### Post by Bothered on 2007-12-04
When in the install do you encounter this error?

I have seen this error when installing ubuntu from the the alternate CD, selecting manual install and entering a partition size that is larger than the drive.

To partition the drive before the install, I recommend booting from the LiveCD, disabling drive automount (deselecting the check-boxes under removable storage in System->Preferences->Removable drives and media) and then using gparted (System->Administration->Partition Editor).

---

### Post by kajillin on 2007-12-04
> **Bothered said:**
> When in the install do you encounter this error?

I have seen this error when installing ubuntu from the the alternate CD, selecting manual install and entering a partition size that is larger than the drive.

To partition the drive before the install, I recommend booting from the LiveCD, disabling drive automount (deselecting the check-boxes under removable storage in System->Preferences->Removable drives and media) and then using gparted (System->Administration->Partition Editor).

Okay well i tried that, everything went okay until the partitioning was done then it just went back into unallocated space. No longer letting me partition it.

Im going to just download the text based installer and see if i get better results. I know my drive isnt !$@#ed because i was just using it today when i decided to come back to linux.

---

### Post by hyper_ch on 2007-12-04
Can you just wipe the whole drive?

---

