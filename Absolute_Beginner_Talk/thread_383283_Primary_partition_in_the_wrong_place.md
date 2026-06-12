---
title: "Primary partition in the wrong place"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2007-03-13
The screenshots should tell you bunches. I don't recall how or when this happened, but I have Dapper loaded in a teeny partition squished at the back end of my slave drive, with a pretty small swap as well.

Not only do I keep getting error messages about insufficient space for a standard distribution upgrade, but also the partitioner on both the Edgy and Feisty Live CDs refuse to take advantage of that juicy 26GB space on the "a" drive. Not enough space, it says.

I'm unsure what's up here. Although I use Ubuntu (Feisty) exclusively at work, here on this comp it's mostly XP (hda1). In other words, I don't as yet have any important files outside of the XP partition that I'm concerned about... I'd like to know how to overwrite all of Dapper, dual boot from the first disk, and have hdb be just extra storage for Edgy or Feisty.

Thanks in advance for any help.

P.S. - Is there a way for me to just scoot the Dapper install over to the unallocated section of hda? That would be ideal!

---

### Post by hyper_ch on 2007-03-13
Hmmm, you have a lot of unallocated (non-partitioned) diskspace... on the partition where you have ubuntu installed you could enlarge it (as there is free space)...

---

### Post by PartisanEntity on 2007-03-13
> **ricardisimo said:**
> I'd like to know how to overwrite all of Dapper, dual boot from the first disk, and have hdb be just extra storage for Edgy or Feisty.
!

Insert the Dapper live cd into your cdrom drive and boot the computer from this cd.

Once the live cd desktop has loaded, you can launch gparted.

You can then click on this small partition (make sure you are on hdb) and delete it.

Then you can create a new partition and choose ext2 or ext3 file system.

gparted is quite simple and the options are self explanatory, but if there is anything you don't understand just post back.

The important thing is to make sure you are viewing the right hard disk before you edit the partitions :)

---

