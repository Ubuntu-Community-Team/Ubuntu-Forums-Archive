---
title: "Getting rid of ubuntu (temporarily)"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by mekadaboss on 2008-02-17
I installed ubuntu on a computer but I want ubuntu on a different computer. but before I install it I want to make sure I can get it off the first one before Install it on the other. so how do I get rid of ubuntu and keep my xp os and files.

---

### Post by oldb0y on 2008-02-17
Delete the Ubuntu-partition, and then add it to your XP-partition

---

### Post by cmnorton on 2008-02-17
Is there a special requirement that makes you want to uninstall? For example, are you worried someone else will use it? Do you want to reclaim the hard-drive space for XP?

You can install Ubuntu on an infinite number of computers; there is no limit.


The easiest way to uninstall it would be to boot using a live CD, mounting the drive on which you installed Ubuntu, and removing the partition with fdisk. Just make sure you identify files on this partition and make sure they are not XP files before you delete the partition. Then, assuming you'd want XP to use this partition, you would have to reformat it in XP.

---

### Post by mekadaboss on 2008-02-17
do I do that in xp or ubuntu or ubuntu live cd?

---

### Post by mekadaboss on 2008-02-17
all right I'll go try that

---

### Post by oldb0y on 2008-02-17
Use the Live CD, and just do as cmnorton says.

---

### Post by LaRoza on 2008-02-17
You will not be able to boot XP if you follow the advice on this thread so far.

First you will need to restore the Windows MBR. If you don't have another method, use the Super Grub Disk. See the link in my sig. The option to restore the Windows MBR is under Advanced->Windows (Advanced) and is the first option. You will have to boot from the SGD.

After doing that, reboot the computer. XP should load with no hint of Ubuntu. From XP, go to Computer Management->Disk Management and delete the Ubuntu partitions and grow the Windows partition to fill that space.

---

### Post by cmnorton on 2008-02-17
> **oldb0y said:**
> Use the Live CD, and just do as cmnorton says.

...but be very very careful. cmnorton once was trying to image the physical drive in his carefully installed and configured Fedora workstation (one used for work) to a USB drive, and wound up deleting the files on the workstation.

Live disks are nice, but using them requires a moment to breath and get your bearings. You'll want to mount the Ubuntu partition just to check the files to verify which partition you are going to destroy. You can run sudo fdisk -l to get an output similar to this:

sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20552055

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4680    37592068+  83  Linux
/dev/sda2            4681        4865     1486012+   5  Extended
/dev/sda5            4681        4865     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x579b42a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19929   160079661   83  Linux
cnorton@h2oworks:~$ 

However, I don't have an output for you booting from a live CD, and do not know quite how your drives are going to look from that configuration.

There are partitions on each disk. You'll need to run man fdisk and info fdisk, before doing any of this. If this were a test system, I'd say go for it. Given you have XP installed on this system, I'd say install another disk, and leave this partition alone. If you don't mind making mistakes and perhaps re-installing XP, then go for it, but be careful.

... and back up everything you hold dear on both the Ubuntu and XP disks before doing anything.

---

### Post by cmnorton on 2008-02-17
> **LaRoza said:**
> You will not be able to boot XP if you follow the advice on this thread so far.

First you will need to restore the Windows MBR. If you don't have another method, use the Super Grub Disk. See the link in my sig. The option to restore the Windows MBR is under Advanced->Windows (Advanced) and is the first option. You will have to boot from the SGD.

After doing that, reboot the computer. XP should load with no hint of Ubuntu. From XP, go to Computer Management->Disk Management and delete the Ubuntu partitions and grow the Windows partition to fill that space.


Good advice. Would removing the partition alter his MBR?

---

### Post by mekadaboss on 2008-02-19
thanks a lot LaRoza that worked great and i still have all of my data.

---

