---
title: "Cloning a dual-boot hard disk"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by Paul_UK on 2006-10-01
I have a dual-boot arrangement with Windows XP and Ubuntu 6.06 on a 40GB hard disk in my laptop.

I have four partitions:

/dev/hda1 - 13.8GB NTFS for Windows XP
/dev/hda2 - 13.8GB ext3 for Ubuntu
/dev/hda4 - 8.8GB FAT32 for my documents etc used by both operating systems
/dev/hda3 - extended containing 
- - /dev/hda5 - 815MB linux-swap

I want to transfer the whole lot onto an 80GB hard disk, increasing the sizes of hda1 and hda2 to around 20GB and hda4 to take up the rest.

I have tried connecting the drive to another PC and making an image file with Norton Ghost 2003, then tried restoring that image to the new drive, but it failed complaining that most of the disk was unwritable (the drive is good and was successfully wiped with dban).

What is the best way to do wat I want to achieve, without reinstalling everything again from scratch?  Both operating systems are recent installs and are working nicely - I just need more space especially for the shared FAT32 partition.

Thanks.

---

### Post by davmac on 2006-10-02
My initial response was going to be partimage, which is available in the repositories, but I don't think it handles NTFS. I believe that Acronis TrueImage handles both NTFS and linux partitions successfully but I haven't used it myself.

You might be able to use a composite approach with partimage for Ubuntu and something like xxcopy with the /clone option (see [http://www.xxcopy.com/](http://www.xxcopy.com/)) for Windows.

Hope this helps,

Dave Mac

---

### Post by Paul_UK on 2006-10-02
Thanks Dave.

I will be away for a few days but have downloaded a demo copy of Acronis TrueImage to look at.  It says it's fully functional for 14 days - if that's true I won't need to pay for it (somehow I doubt the demo will actually let me clone a disk though...).

I'll let you know how it goes.

Paul.

---

### Post by Paul_UK on 2006-10-14
Acronis TrueImage worked fine, thanks.  The demo version did the job - no need to spend any money!!!  :D

---

### Post by CatKiller on 2006-10-14
I'm glad you managed to get it done. For future reference, it's possible to do it entirely with the live cd. The two tools that you need are **dd** and **gparted**.

The first step is the one that takes ages. Assuming you've got the current drive in as Primary Master, and the larger drive as Primary Slave, the command ```
dd if=/dev/hda of=/dev/hdb
``` will do a bit-by-bit copy of your current drive, MBR and partition table and all, onto your larger drive. Then you can use gparted to shuffle and resize your partitions on the new drive.

---

### Post by mulligan.can on 2006-12-24
I know, this is an old thread. However I just wanted to say a few things. Firstly, the search feature is brilliant, had the same question and this saved me making my own thread. Secondly, dd is a decent tool to migrate to a new hdd right? Just wondering if there is anything that would do the job betterer :).

Anyway, thanks :)

---

### Post by Frank Golden on 2006-12-24
> **mulligan.can said:**
> I know, this is an old thread. However I just wanted to say a few things. Firstly, the search feature is brilliant, had the same question and this saved me making my own thread. Secondly, dd is a decent tool to migrate to a new hdd right? Just wondering if there is anything that would do the job betterer :).

Anyway, thanks :)
I have used Partimage for the linux partition and Ghost 9 for XP with success.

---

### Post by pseudonym on 2006-12-24
> **davmac said:**
> My initial response was going to be partimage, which is available in the repositories, but I don't think it handles NTFS. 
Not true! I've saved and restored ntfs partitions twice with partimage without any problems (it spits out a warning about ntfs support being 'experimental', but you just ignore that).

I highly recommend using the [System Rescue CD]("http://www.sysresccd.org/Main_Page") for this purpose. It's got partimage and a stack of other useful tools and boots up in an instant. The beta version has a slightly more recent kernel if your system is a fairly new one, too.

---

### Post by mulligan.can on 2006-12-24
Ok, cool, thanks. I shall have to look into  System Rescue CD. At present dd seems to be working ok :)

---

### Post by smoker on 2006-12-24
the gparted boot cd can copy partition to partition, then partitions can be resized to suit.

---

