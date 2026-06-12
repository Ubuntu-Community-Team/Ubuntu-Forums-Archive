---
title: "fsck problems"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by pmcastillo on 2008-03-24
I did a little fsck, and this is what I saw:

```

pmcastillo@pmcastillo-desktop:~$ sudo fsck -n
[sudo] password for pmcastillo:
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Warning!  /dev/sda6 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
/dev/sda6 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 1346595 has zero dtime.  Fix? no

Inodes that were part of a corrupted orphan linked list found.  Fix? no

Inode 1346598 was part of the orphaned inode list.  IGNORED.
Inode 1346599 was part of the orphaned inode list.  IGNORED.
Inode 1346600 was part of the orphaned inode list.  IGNORED.
Inode 1346601 was part of the orphaned inode list.  IGNORED.
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong (1836016, counted=1835934).
Fix? no

Inode bitmap differences:  -1346595 -(1346598--1346601)
Fix? no

Free inodes count wrong (1329545, counted=1329509).
Fix? no


/dev/sda6: ********** WARNING: Filesystem still has errors **********

/dev/sda6: 146839/1476384 files (1.2% non-contiguous), 1115919/2951935 blocks
pmcastillo@pmcastillo-desktop:~$ 

```

How can I fix this thing?

---

### Post by Locutus_of_Borg on 2008-03-24
Choosing yes when it asks you if you want it to fix the problems is a good start...

---

### Post by pmcastillo on 2008-03-24
I did a little research on **fsck** and almost 99.9% of them said: "It is not a good idea to fix while it is mounted". That's why I'm a little scary to choose **"yes"**. But when I try to  unmount **sda6**, it won't let me saying something about "sda6 is busy". Maybe because it is my OS.

So I don't have an idea how to unmount it, to get the fsck working....

---

### Post by dcstar on 2008-03-24
> **pmcastillo said:**
> 
.........
So I don't have an idea how to unmount it, to get the fsck working....

```
gksudo gedit /etc/default/rcS
```

Make FSCKFIX=yes.

That will automatically answer Yes for fsck at boot time.

To fix your system, boot off the Ubuntu CD and use the Partition Manager to fix it.

---

