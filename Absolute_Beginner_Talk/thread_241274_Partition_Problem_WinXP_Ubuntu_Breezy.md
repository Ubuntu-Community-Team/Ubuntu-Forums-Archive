---
title: "Partition Problem WinXP Ubuntu Breezy"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by doodsangel on 2006-08-22
Good day,

For the past weekend I have tried to install Ubuntu. First release 4, and then got hold of a copy of ver 5 (Wanted to get latest version from the freedomtoaster @ tuks, but alas they are only open in the day)

My problem is as follows: I am unable to create a partition to install Ubuntu to. 
I have WinXP as First Primary Partition, thereafter I have a 30G space free before my other partitions begins(where I'd like to install Ubuntu). When it goes to the partitioning tool, it gives me a couple of options but **none is working**, except the ones for deleting my whole 120Gb drive and start from scratch, which I definately do not want to do. I am unable to pick up any partitions or the free space during install, but when I run the live CD, it mounts all my partitions without a problem.

I seriously need help.

My next course of action I have thought of, was download GPart ISO image and creating the Ubuntu partition prior to inserting the Ubuntu installation CD, and first create an Ubuntu partition and then try to install. Would this work?

Any ideas would be welcome.

I thank thee in advance.

---

### Post by birdbrain on 2006-08-22
You may need to partitions, 1 small parition for your swap drive and another for your root install. It is also possible that you may need to boot into the live cd, umount the paritions you want and use fdisk

WARNING, if you use the wrong parition, eg your windows partition you could loose data. Just starting fdisk won't do any harm but the later steps may if you choose the wrong partition.

1. fdisk /dev/hda
2. type p to get a listing
3. note the number of the parition you want and then press t (for type)
4. set the type to 83
5. press w to write the changes to disk

P.S you should also have a smaller partition of between 512 and 1024MB for your swap space. If you setup you swap space then change the type of that partition to 82

Now you can format your paritions
Lets say that /dev/hda2 is swap then typing:
mkswap /dev/hda2 would setup hda2 for swap

# WARNING - This is the step that would stuff your data up if you have the wrong partition.
If you wanted reiserfs for say /dev/hda3 you could type
mkreiserfs /dev/hda3

You could then try and reboot and use /dev/hda3 for root i.e / and /dev/hda2 for swap.

---

### Post by doodsangel on 2006-08-22
I have downloaded GParted. As per the documentation, it tells me that it is not useable with "logical volume type of disk organisations", is this not what LVM is that Ubuntu uses. 

Please? Any help offered will be appreciated.

Is there a way of installing Ubuntu 5 without using LVM manager and just create ext3 and swap space partitions and feed the installer some commands to use the partitions I have specified?

---

### Post by doodsangel on 2006-08-22
Thank you **birdbrain**

Will try that tonight.

---

### Post by doodsangel on 2006-08-23
I have tried gparted, but it didn't work, thereafter I tried fdisk as birdbrain suggested. I was able to create and format the partitions. 
/dev/hda5 <- suppose to be root "/"
/dev/hda9 <- swap space
/dev/hda10 <- planning on making this home.

Ran Ubuntu 5.10 installlation again. Once again the Ubuntu partition tool was unable to pick up any partitions, only giving me the option to destroy my complete harddrive and start from scratch. I tried professional installation next, and skipped the partition bit. When I told it to install, it said noe "/target" specified. I then ran the shell tool, and did a "mount /dev/hda5 /target", and tried the install again. I was quite excited to see Ubuntu install, only to be dissapointed after restarting.

GRUB came up, and gave me all the choices I wanted, but when I tried to boot into Ubuntu, I got the following:

[B]Booting 'UBUNTU, kernel 2.6.12-9-386'

root(hd0,0)
Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash

Error 17: Cannot mount selected partition.

Press any key to continue.[/B]

Now, I can clearly see that "root=/dev/hda1" must be wrong as it is supposed to be /dev/hda5. Now how do I fix this and how do I specify the operating system to use /dev/hda10 as "/home", as I suppose that will also be wrong. ](*,)

---

