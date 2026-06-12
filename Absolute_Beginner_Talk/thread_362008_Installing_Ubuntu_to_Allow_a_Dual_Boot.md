---
title: "Installing Ubuntu to Allow a Dual Boot"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by General Skanky on 2007-02-15
I have installed Ubuntu in the past on a completely formatted disc. That was easy.

I have now partioned my laptop 65Gb for Windows and 25Gb free to install Ubuntu.

The question is how do I do it? Ubuntu sees the HDD as a whole 100Gb for auto install or I can do a manual install. How? I can't work it out.:confused:

---

### Post by colonelk on 2007-02-15
Install Windows first.  Then after it is installed use your Ubuntu Live CD and install from that.

It will configure GRUB which will allow you to select which OS you want to run when you boot up.

If you install Ubuntu first, Windows overwrites the Boot record and doesn't give you the option of booting into ubuntu!

Edit:  If you have already partitioned your disk using something like Fdisk or equivalent before installing an OS then you needn't have bothered. Both Windows and Ubuntu allow you to repartition/Format as part of their OS installation routine, Windows with Xp/Vista setup and Ubuntu with Gparted.

All you need do is make sure when you install windows you only configure part of your disk as NTFS or Fat32 (the bit you want to use for windows).  Leave an amount of your disk completely unformatted for Ubuntu and then in its installation routine Gparted will allow you to choose which file system you want to run ubuntu on.

HTH

---

### Post by ashmew2 on 2007-02-15
since uve already thought of the sizes u want to allocate to windoze and Ubuntu , just select Manual Partition from the Live CD(when u start installing Ubuntu).
Your windows partition (C: Drive) will most likely be at /media/hda1 , and the other drives (D , E , F) after that (/media/hda5,/media/hda6,so on). So after these partitions u have the space in which u will install Ubuntu , remember to format them as ext3 (Ubuntu uses this file system).

PS : it will be best if u have all ur other drives as FAT32 because NTFS writing is still not well enuf in UBuntu (i think so)

Ask if u need anythin more :P

---

### Post by rai4shu2 on 2007-02-15
It sounds like you're ready, but you still probably want to set up a swap partition. You can do that with gparted or whatever Linux partition application you're comfortable with. You might also consider dividing the Ubuntu into two partitions: one for root and one for home (i.e. / and /home).

Then, when you want to install, you should choose Manual and be sure that the partitions are marked appropriately before the installer continues to the install step. Just remember (or write down) how you set them up with gparted before you run the installer.

---

### Post by zvacet on 2007-02-15
In the installing proces you will come to the partition step.Choose to partition your disc manualy,and you will see free partition.Install Ubuntu on it.Split your free partition to 10-15GB(your choice) for root,most of rest for home.Of course you need swap partition(virtual memory) but depends on your comp.I hope this will help you,and you will be join Ubuntu.

---

