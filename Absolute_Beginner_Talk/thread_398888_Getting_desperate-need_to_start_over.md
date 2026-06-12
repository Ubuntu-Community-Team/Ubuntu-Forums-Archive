---
title: "Getting desperate-need to start over"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by flooperer on 2007-04-01
This should be simple, but I've been trying hard for four days and gotten nowhere.

I installed feisty on my whole drive. I need to start over and install windows xp, then reinstall feisty as a dual boot.

But after installing feisty I can't return my disk to a state where windows xp will detect it. I have tried a lot of things, and looked at many helpful posts but am still, absolutely, at square one.

I feel like there is something simple I'm missing. I don't need to preserve any data, or any OS, I just need to get windows xp to detect my disk.

Please help!!

---

### Post by oilchangeguy on 2007-04-01
i hate to ask this, but is the computer set to boot from the cd drive? and what does the error message say when you try to load windows?

---

### Post by johnc4510 on 2007-04-01
Try downloading the gparted live cd from this web site:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Burn it to a cd then boot to it. You will be able to repartition your hard drive for Windows and Ubuntu.

Hope this helps.

---

### Post by flooperer on 2007-04-01
Yeah, I can boot off the CD drive, but when I get to the blue screen with the option - hit enter to install windows-
 I hit enter but then get a message 

"there are no hard drives installed, setup cannot continue"

I've tried adding NTFS and FAT32 partitions, and I used Fdisk /mbr too,

no dice. 

Windows xp just can't detect the drive. I've tried different xp disks and home and pro versions.

---

### Post by OMRebel on 2007-04-01
Have you tried just a good 'ol Win 98 bootdisk and run fdisk?

---

### Post by oilchangeguy on 2007-04-01
how many people have a 98 boot disc still laying around? and even more important, how many know how to use it correctly? yes you can use fdisk to delete the partition, if you know the steps (i do).

---

### Post by wpshooter on 2007-04-01
> **oilchangeguy said:**
> how many people have a 98 boot disc still laying around? and even more important, how many know how to use it correctly? yes you can use fdisk to delete the partition, if you know the steps (i do).

I do, wouldn't be caught without one !!!  Still very handy after all this time.

---

### Post by flooperer on 2007-04-01
I don't have a win 98 disk, but I used an old Dell utility CD that has fdisk on it. I tried fdisk on the main drive and the MBR. I also formatted the whole drive from DOS. We tried symantec ghost over a network, and boot and nuke.

---

