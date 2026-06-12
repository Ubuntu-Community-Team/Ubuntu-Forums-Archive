---
title: "Fat32 ; Ext3 ; Swap ; Id7"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by Dutch on 2006-01-26
Hi I've got a new  PC:
P4 3Ghz 500MB 80 GB met XP pre-installed

I understood:

FAT 32 =  for Ubuntu and XP
EXT3 = for Ubuntu
SWAP (ID82) is for what ?
XP partition ( ID 7)

I also would like to have a backup HD for XP and Ubuntu
I tried to prtition the 80GB HD with
sudo cfdisk /dev/hda

But I don't know how.

For the FAT32 I want to use 20GB
XP I want to use 10 GB

How much does the SWAP needs ?
And how much does Ubuntu needs ?

For the back up I need XP=5GB and Ubuntu 10GB

How can I make these partitions ?

XP is already pre configurated.

---

### Post by Adrian on 2006-01-26
[QUOTE=Dutch]SWAP (ID82) is for what ?
[/QUOTE]
Usually your RAM isn't large enough to contain all programs, data and so on. The most common solution is to move ("swap") less frequently used parts of the RAM to disk (to free some RAM), and then move it back to the RAM when it's needed. 
The swap partition is a small partition used for this.

> How much does the SWAP needs ?
Your amount of RAM multiplied by 1.25 should be enough.
I.e., if you have 256MB RAM, a swap partition of 320MB is a good choice.

> And how much does Ubuntu needs ?

Always a tricky question :)
The cover of the install CD says that at least 1.8GB is required. 
You'd probably want more than that. 5 GB is usually enough for me, but that is very individual.

> 
How can I make these partitions ?
I always use the partitioner on the Ubuntu install CD (which runs when you install Ubuntu). It handles most operations, including resizing partitions.

---

