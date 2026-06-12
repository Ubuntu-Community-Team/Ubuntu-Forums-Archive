---
title: "How to partition ubuntu onto a seperate partition, leaving backup partition untouched"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by jashan17 on 2007-10-06
Im new to linux, i just installed linux through the live cd because i had a partition on my hard drive that i wanted to burn to discs, because i formatted my c: drive. So i have ubuntu, and im in the installer window. I want to manually set up my partitions so that i can install ubuntu onto hda1 and not touch hda5 with my important files on it. my hda5 is ntfs and it says mount point /media/hda5? i dont know what that means but i just want to run linux straight from hda1. How would i go about editing the settings for each partiton if i want this?

---

### Post by bodhi.zazen on 2007-10-06
That is the mount point, or where the data will be mounted after you install.

The defaults are fine, JUST DO NOT FORMAT hda5 and you will be fine ;)

This link might help :

basic partitioning : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by jashan17 on 2007-10-06
So do i still go on and do it customly? or do i check use entire hard disk?

---

### Post by kellemes on 2007-10-06
No, this way the hole disk (including hda5) will be used to install Ubuntu.
You can use all the other space/partitions and **not** hda5.. So when it says mount point /media/hda5.. that's fine. It only means it will be available to you when you boot into Ubuntu.
Just don't install Ubuntu on the hole disk, becuase hda5 will be a part of this.

Edit: There is a difference between using a partition to install part of the operating-system, and often reformat and copy a bunch of files on it etc.. **and** simply mounting the partition, mounting does no harm to data on the partition/disk.

---

### Post by jashan17 on 2007-10-06
But which ones do i set as the swap discs and stuff, im pretty confused and am completely new to it lol. And when i click next it says no root file system is identified. Can i use the hda1 as a swap? will that work?

---

### Post by jashan17 on 2007-10-06
So the setup is like /dev/hda1(my empty one) swap 52843 MB Unknown
                      and /dev/hda5(my backup one) ntfs /media/hda5 67187 mb unknown

Good?

---

### Post by kellemes on 2007-10-06
You can basicaly delete all partitions (including hda1) .. just leave hda5 alone.. See to it it's not touched, not formatted etc.. keep off. :popcorn:
Then let the installer use the empty space to install itself.. as far as I know it will setup it's partitions automaticaly. And since it will use the empty space it ill not use hda5.. this is what you want.

You can also create 3 partitions yourself (manual partition), order doesn't matter... just one example of a setup:
- swap-partition 2 times your memory with a maximum of 2Gb.
- / (root) partition of about 10Gb
- /home partition of -whatever you want- size (mine is 15Gb)

Just let those partitions be formatted as ext3.

---

### Post by jashan17 on 2007-10-06
How woud i let the installer use the free space to install itself. Which option do i click on? I deleted Hda1 partition. when i click next it says no root file system identified...
And what do you mean by /(root)  partition and /home partition...Which partitions should be ext3?
EDIT: I think i figured it out now, thanks for all the help. :)

---

### Post by bodhi.zazen on 2007-10-06
See if this helps 

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by jashan17 on 2007-10-06
Language: English
 Keyboard layout: U.S. English
 Name: Jashan Makan
 Login name: jashan
 Location: America/Edmonton
 Migration Assistant:



If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 IDE1 master (hda)

The following partitions are going to be formatted:
 partition #7 of IDE1 master (hda) as ext3
 partition #8 of IDE1 master (hda) as ext3
 partition #6 of IDE1 master (hda) as swap


Is that alright? , my partition 5 is my backup, so it will not be deleted?

---

### Post by bodhi.zazen on 2007-10-07
Looks good to me ....

---

