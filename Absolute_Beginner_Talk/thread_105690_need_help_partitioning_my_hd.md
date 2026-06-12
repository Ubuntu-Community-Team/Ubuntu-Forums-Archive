---
title: "need help partitioning my hd"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by stroopwafel on 2005-12-18
i have a 20.5 GB Maxtor 2B020H1 hard drive on a ibm celeron (800Mhz) desktop.

I just started installing ubunto from a downloaded install (not live) cd.

I encountered the first problem in the partitioning step:
The partitioning failed: (something like: failed to set up ext3 ....) so I tried the LVM option in the guided partition. (don't know what it means) and this worked.

Now I encounter a problem when I load the LILO: It fails to put it on the disk.

My Hard drive partitions are a mess now. How do I undo the partitions and start all over?

What should I do to run LINUX on my computer: try a different distribution?

---

### Post by stroopwafel on 2005-12-19
ps:
the actual error was: The ext3 file system creation in partition #1 of the IDE master (hda) failed.

---

### Post by earobinson on 2005-12-19
> My Hard drive partitions are a mess now. How do I undo the partitions and start all over? Just reinstall, the partition process will wipe the old data clean

Are you doing a normal install, I was under the impresion grub was the default boot loader for ubuntu?

---

### Post by stroopwafel on 2005-12-19
I am doing a normal install.

What are the consequences of my chosing the LVM option?

---

### Post by earobinson on 2005-12-19
[http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29)

nothing that I know of.

---

