---
title: "trouble understanding Mac OS partitions"
date: 2007-09-21
forum: Apple PPC Users
---

### Post by molly_001 on 2007-09-21
Hello -- Thanks for reading.

I have installed Ubuntu on dozens of x86 machines and now I am studying up and preparing to install Ubuntu on an iMac G3 PPC 500 MHz with OS 9.2.

I'm proceeding carefully since I'm not familiar with the Mac OS file system.
Please look at the items below.  Can you help me understand why the Ubuntu installation picks up on 5 partitions?  Do you know what these partitions could be?

Here is what I get when I have a look-see using the MAC OS X DISK UTILITY, PARTITION EDITOR TAB:

Quantum Fireball lct15 30      on ATA Device 0
28.00 GB
It offers only one partition in the current state, which of course is the Mac OS partition.  It mentions no other partitions.

HOWEVER, here is what I get when I use the Alternate Install CD for PPC of Ubuntu.  In the Detect Disks --> Manual Partition area:
#1   32.3 kB  Apple
#2   32.8 kB  Macintosh
#3   32.8 kB  Macintosh
#4   262.1 kB  Patch Partition
#5   30.0 GB   hfs+   Mac OS
then 5.1 kB FREE SPACE

Thank you!

---

### Post by frog_pilot on 2007-09-21
the small partitions contain mac-partitiontable, os9 driver and so on. These much partitions are normal on a macintosh-system-volume. The mac needs all these partitons and free spaces.

On Apple-Partiton-Table drives you dont have the Limitations like on Dos-Partition-Tables. The mac can manage 12 or more primary volumes on a harddrive.

You should turn off journaling on your system-volume and let the ubuntu-installer do the job automatically. Or shrink the big volume which is surely your system-drive and take the new free space. You will need at last 3 partitions: 1 new-world-boot-partition where the bootloader yaboot is located and root and swap as you will know.

Ubuntu on a mac is something completely different then ubuntu on x86... :popcorn:

---

### Post by molly_001 on 2007-09-21
Thanks very much, frog pilot.
That was all extremely helpful !!

---

