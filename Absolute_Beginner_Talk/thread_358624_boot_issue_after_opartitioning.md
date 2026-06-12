---
title: "boot issue after opartitioning"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2007-02-11
Well ......

All was well. I had a boot partition, and a data partition. My home partition was within an extended partition with my swap partition.

I copied all data from the data partition to the home partition and using GPartEd deleted the data partition and extended the extended partition and then the /home contained therein to have three partitions;

boot
extended - containing /home and swap.

My system will now not boot!!

I get the Ubuntu Flash loader, then 'dos' screen telling me;

Activate Swap - OK
Check File System - OK
... THEN;

FSCK.EXT2: ENABLE TO RESOLVE UUID- *^%$%$@&^(.......

FSCK DIED WITH EXIT STSTUS 8
FILE SYSTEM CHECK FAILED.

I AM LEFT WITH A PROMPT THAT I DO NOT KNOW WHAT TO DO WITH!

I am eating :popcorn: and entertaining myself :guitar:awaiting guidance from those more knowledgeable than I !!!!:lolflag:


Tony

I need guidance please!

---

### Post by tchoklat on 2007-02-11
I fixed it myself. I removed the UUID reference in the fstab to the partition I removed and all is cool !!!

---

