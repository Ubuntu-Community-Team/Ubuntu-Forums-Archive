---
title: "In the middle of a install, need help quick! - URGENT"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by virtuexru on 2006-06-23
Ok, so I'm installing UBUNTU on my Laptop with Windows XP on it. I'm in live CD Mode right now and it works perfectly.

I started install but am having problems with partitioning my drives. I read some tutorials but am still stuck because there seems to be something wierd with my partitions. It says I cannot create more than four.

I am trying to setup a dualboot system. Here is what I see... What should I be doing? I have a 90GB HD.

I want to make a SHARED space thats about 20GB.

I have :

dev/sda1/  ntfs  /  6GB
dev/sda2/  ntfs  /  39GB (BOOT)
New Partition #2 /  ext3  /  20GB
New Partition #3 /  linuxswap  /  2GB
unallocated /  26GB

---

### Post by aysiu on 2006-06-23
You can't create more than four primary partitions. But you can have a lot more extended partitions.

---

### Post by virtuexru on 2006-06-23
How do I go about doing that? Changing a NFTS to a EXTENDED?

---

### Post by aysiu on 2006-06-23
I don't think you can just change a primary to an extended. I think you'd actually have to delete one of your primary partitions and create a new extended one.

---

### Post by virtuexru on 2006-06-23
So should I delete the first one which is the smallest? It doesn't have the BOOT tag on it.

---

### Post by aysiu on 2006-06-23
I'd delete swap and Ext3 and then create three extended partitions--one for swap, one for /, and one for your shared space.

Have you read this?
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by virtuexru on 2006-06-23
Will this affect the new installation in a negative way? Should I just screw the shared and keep it at Windows/Unbuntu/Linux-Swap ?

Sorry for all the questions. :\ Just want to make sure.

---

### Post by aysiu on 2006-06-23
Well, the partitioning process happens *before* you actually format the Ubuntu partitions, so I would say it's much safer to delete the Ubuntu partitions than your NTFS ones (which probably have data on them).

---

### Post by virtuexru on 2006-06-23
Should I just let the UNBUNTU installer format the crap for me so I could dual boot? OR should I just go with

NFTS Windows Partition
Linux Partition
Linux Swap

---

### Post by aysiu on 2006-06-23
It doesn't make sense to have 26 GB of ununsed space. I think you should delete the Ext3 partition. Delete the swap partition. Then, create three new partitions--one Ext3, one swap, and one FAT32. Make them extended instead of primary.

---

### Post by virtuexru on 2006-06-23
OK.. so now I have this.. is this correct?
[B]
Two NTFS partitions (primary's) totalling 45GB.
An EXTENDED 20GB Partition containing
   -   Partition EXT3 18GB
   -   Partition LINUX-SWAP 2GB
A PRIMARY FAT32 30GB Partition[/B]

---

### Post by aysiu on 2006-06-23
Sounds good. Go for it.

---

### Post by virtuexru on 2006-06-23
[QUOTE=aysiu]Sounds good. Go for it.[/QUOTE]

Alright. Thanks for all the help. Here I go!!!

---

### Post by virtuexru on 2006-06-23
[QUOTE=virtuexru]Alright. Thanks for all the help. Here I go!!![/QUOTE]
:confused: 

Got an error in creating Partition #3 (the EXT one).

Damnit.

---

### Post by aysiu on 2006-06-23
What's the error?

---

### Post by virtuexru on 2006-06-23
[QUOTE=aysiu]What's the error?[/QUOTE]

I don't remember I don't think it said, it just said Error creating the extended partition. I'm back in Windows, wanted to make sure I didn't mess anything up.

---

### Post by virtuexru on 2006-06-23
I'm going to try PerfectDisk to defragment, maybe I can get rid of that extra partition or something? Hopefully this will help. If not I guess I'll have to live without a FAT32 Shared partition.

---

