---
title: "Absolute beginners guide to running dualboot Edgy?"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Visti on 2007-01-12
Hi, I've never had a Linux dist. running on my comp. before, so I've decided a dual boot system is probably the best way to test it out before I might get something like a dedicated Linux box.

Anyhow, I have two harddrives - One that's currently running XP and another that's got some stuff on it that I would like to keep, but still has about 40+ GBs free. Now, can I partition the available 40+ gbs on the second harddrive while keeping the stuff that's on there and then later splitting that partition into swap and so on?

What would be the best way for me to go about doing something like this? Using the partition program in the Ubuntu Live CD or using a windows-based one?

Also what exactly would I end up with partition-wise? As far as I understand it would be something like:

Harddrive with XP (NTFS)
Different windows stuff (ntfs)
Main Ubuntu (10+gb, but FAT?)
Swap (1gb, FAT?)
Shared FAT32 (6-7gb, FAT32)

Is that right at all? And anything I should be particularly cautious with in this setup?

---

### Post by jvc26 on 2007-01-12
Here is a link to a really helpful page on installing Ubuntu:
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
If you look down the links on the side you should find all the information you need :)

> **Visti said:**
> 
Harddrive with XP (NTFS)
Different windows stuff (ntfs)
Main Ubuntu (10+gb, but FAT?)
Swap (1gb, FAT?)
Shared FAT32 (6-7gb, FAT32)

Just 2 things, Swap will be formatted as swap, and I would recommend you putting your main Ubuntu partition as ext3. You have a shared file area (FAT32) which will allow shifting between the two OSs so I'd probs just put the Ubuntu on an ext3.

Il

---

### Post by CroEragon on 2007-01-12
If you have never booted any Linux, i would strongly suggest to first try out LiveCD. Many things are different in Linux and until you are completely used to Ubuntu. Then defragment drve that will be partitioned at least 2 times so you do not have any problems. Then just resize existing partition and leave unallocated space. Ubuntu partitioner will take care of creating partitions. Do not create do not create main Ubuntu and swap partition. just leave unallocated, Ubuntu will create best partitions for itself. About shared partition, i would recommand tu use ext3 filesystem and FS Drvive (google it) to acces ext3 filesystem from windows. Fat32 gets fragmented easily. Or make it ntfs and then use ntfs-3g drivers for linux.
If you have any further questions, just fire away we will try to answer.

---

### Post by shareMenaPeace on 2007-01-12
Can it be that ntfs-3g driver no longer needed?
I can access ntfs without installing ntfs-3g.

---

### Post by Sef on 2007-01-12
> Main Ubuntu (10+gb, but FAT?)
Swap (1gb, FAT?)

Main Ubuntu should be ext3, the default file system.

Swap should be swap-linux.

---

### Post by Frank Golden on 2007-01-12
> **shareMenaPeace said:**
> Can it be that ntfs-3g driver no longer needed?
I can access ntfs without installing ntfs-3g.By access do you mean read/write?
NTFS has always been accessible read only. But not write without third party support.

As to the original topic see this for much info about dual booting.

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

---

### Post by Visti on 2007-01-13
For some reason I can't get the intergrated isntaller partitioner to use uallocated space on my second drive - the partitioning seems to fail. Both if I allocate the space myself and if I use the automatic partitioner. The manual says fail and the automatic just keeps loading forever when I press 'forward'

I just remembered that I forgot to defrag the second drive.. Could that be it? Also, could I use a windowsbased partitioner to make the partitions?

---

### Post by mikewhatever on 2007-01-13
I doubt, defragmentation has anything to do with unallocated space. Remember that you can only have 4 primary partitions. If you already have 4, then newly created partitions must be extended.

---

### Post by Visti on 2007-01-13
I don't have any partitions right now, I just have one main drive HDa with XP on it and a second drive HDb with various files on it, so I should be able to split HDb up, right?

---

### Post by Visti on 2007-01-13
Right, so now I've tried running Norton Partition Magic to do it, since it has options for both EXT3 and Linux Swap and this is the error that I get:

#1529 Information mismatch in directory entry
A file attribute stored in a file record is different from the attribute stored in its
directory entry. If this error is in a system file (file 0&#8211;10), Windows NT
CHKDSK does not fix it, but Windows NT rebuilds the root directory on the
partition the next time the operating system is started.

I've written a question at the Norton support site about what to do, but maybe somebody in here can help, since it's not a software related problem, apparently.

---

### Post by Frank Golden on 2007-01-13
> **Visti said:**
> Right, so now I've tried running Norton Partition Magic to do it, since it has options for both EXT3 and Linux Swap and this is the error that I get:

#1529 Information mismatch in directory entry
A file attribute stored in a file record is different from the attribute stored in its
directory entry. If this error is in a system file (file 0–10), Windows NT
CHKDSK does not fix it, but Windows NT rebuilds the root directory on the
partition the next time the operating system is started.

I've written a question at the Norton support site about what to do, but maybe somebody in here can help, since it's not a software related problem, apparently.
Try using the alternate CD and the instructions referenced in my earlier post about 
dual booting. For some reason the Live CD fails like this on occasion. 

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

Herman's tutorial is tailored for the alternate CD.

---

