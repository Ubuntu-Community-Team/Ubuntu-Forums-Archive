---
title: "Help setting up"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Wipster on 2006-08-31
Hey I'm rather new to linux and I have a nasty feeling that I have messed up my partitions because I have read alot of things that state I need /usr /boot /tmp /var I only have / and /home (and of course swap) and I have all of mine set to primary because I have no idea what logical is.

Basicly my setup consists of 2 SATA drives one of which I want to use for my movies, pics and music and have it able to share between windows and linux.
Would it be a good idea to put SWAP on another drive to my boot?

The hard drives are 2x 152Gb and I have a gig of ram so any ideas on how my partition table should look?

I stumbled across this sort of map for a windows/linux across multiple drives any thoughts?

Hard Drive 1 (/dev/hda for linux IDE drives)

PRIMARY - Windows - NTFS
PRIMARY - Linux / - EXT3
PRIMARY - Linux SWAP - Linux SWAP
EXTENDED
LOGICAL - Linux /TMP
LOGICAL - Linux /VAR
LOGICAL - Linux /HOME

Hard Drive 2 (/dev/hdb for linux IDE drives)

PRIMARY - Windows Paging - NTFS
PRIMARY - Linux SWAP - Linux SWAP
PRIMARY - WIN/LIN Shared - FAT32

How do I set ubuntu to beable to use 2 swaps because I have read that it greatly increases system performance and what sizes?

Any help would be greatly apreciated.

---

### Post by orb9220 on 2006-08-31
Well mine arn't sata but I dual boot with xp and ubuntu with 2nd drive is a 112gb fat32 that xp and ubuntu share.

1st hd hda1===> ntfs winXP
.......hda2===> / this is root
.......hda3===> /home I have home on seprate partion so if I mess up root  ................and have to reinstall
.......hda4===> swap amd that is it for first HD.

2nd HD.hdd1===> Is my fat32 with my pics,music,etc..

---

### Post by bodhi.zazen on 2006-08-31
You have lots of options and there is no "single answer".

Preamble:
1. Primary vs. Logical. In a nutshell you can only have 4 partitions on a HD, each of these partitions is called a primary partition. One primary partition may be converted to an extended partition which may have 4+ logical partitions within it.

2. I believe you do not need more then the following:
Windows root (C:\)
Ubuntu root (/) [size 15 Gb is likely plenty, anywhere from 10-20 is sufficient)
swap (size = 2x RAM is a standard formula, you likely do not need more then 1 Gb)
Share partition. Easy way is to make this a FAT partition.

You do not need /usr /boot /tmp /var or /home partitions.

I believe you can easily back up /home to your data partition and a separate /home partition is redundant. Others disagree. Dealer's choice.

---

### Post by orb9220 on 2006-08-31
Yes he is right why are you trying to make /usr /boot /tmp /var or /home partitions?

There is no instructions anywhere that tells you to do that. All you need is like the post above. root which is / of 10-20GB is good size. Swap twice the size of ram. Ant your share drive that is fat32 which will destroy any content if it is now ntfs.

Using partiton magic 8 in xp I was able to defrag it and convert to fat32 from ntfs but it isn't foolproof.

---

### Post by orb9220 on 2006-08-31
I have a seprate /home on another partition only as a safety if I mess up my root then when I reinstall ubuntu it won't wipe out my installed programs.

You may or may not want to do this. Otherwise ubuntu auto makes home in root.

---

