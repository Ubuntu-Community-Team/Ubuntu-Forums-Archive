---
title: "Where id hda?"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by yme on 2007-06-16
This feels like such a dumb question to ask but since I upgraded from Dapper to Feisty I can't find the disk of my laptop. In Dapper I think it appeared as /dev/hda1. 

In /dev now there are no hda*. I also looked in /mount and /media. Where has it gone? 

yme

---

### Post by HotShotDJ on 2007-06-16
See if it has become /dev/sda*

---

### Post by yme on 2007-06-16
I can find sda, sda1, sda2, sda5. Why would hda become sda? And given I have a 'basic' install why would there be more than a boot partition and a swap partition? How can I be sure there are my harddrives as I can't click on them?

---

### Post by Happy_Man on 2007-06-16
Feisty changed every HDD from hda to sda during the jump. Don't worry, the HDD is the same, it's just how Ubuntu sees them. I dunno why, though. And perhaps you have extra partitions you have forgotten about?

---

### Post by mcduck on 2007-06-16
Developers found out that SATA drivres handle PATA drives better than the actual PATA drivers did, so they started using those drivers for all hard disks. That also caused all hard disks to be named as sdX instead of using hdX for PATA drives and sdX for SATA/SCSI.

---

### Post by mcduck on 2007-06-16
> **yme said:**
> I can find sda, sda1, sda2, sda5. Why would hda become sda? And given I have a 'basic' install why would there be more than a boot partition and a swap partition? How can I be sure there are my harddrives as I can't click on them?

NO need to worry about them. sda is the disk itself, not partition. Then base on names you probably have primary partition sda1 as root, and then extended partition that contains logical partition for swap.

To check what the partitions are you can run 'sudo fdisk -l' in a terminal.

---

### Post by yme on 2007-06-16
> **mcduck said:**
> To check what the partitions are you can run 'sudo fdisk -l' in a terminal.

Thanks. Everything seems to be OK although there is one small partition matching the size of swap which Ubuntu seems to have added during the default install, I don't know why.

/dev/sda1   *           1        4777    38371221   83  Linux
/dev/sda2            4778        4864      698827+   5  Extended
/dev/sda5            4778        4864      698796   82  Linux swap / Solaris

---

### Post by yme on 2007-06-16
However, now I play around a bit I get the error message:

Error: dev/sda1 is not a directory

It is mounted as dev/sda1, is it not?

yme

---

### Post by HotShotDJ on 2007-06-16
> **yme said:**
> Error: dev/sda1 is not a directoryBecause dev/sda1 isn't a directory.  However, /dev/sda1 is. :)  It is mounted as /  -- pronounced "root" (in a terminal, type "cd /" and then enter (without quotes) and you will see the contents of /dev/sda1 -- don't confuse the root directory with the root user).

The swap partition is a required partition (well, more a highly recommended option -- I'm oversimplifying here).  Almost all Linux distributions will create it by default.  This is a Good Thing (TM) and you should not alter this without very good reason.

---

### Post by sling-shot on 2007-06-16
[QUOTE=HotShotDJ:
 This is a Good Thing (TM) and you should not alter this without very good reason.[/QUOTE]

Now what about THAT?!!!!!!!!!
-SS.

---

### Post by mcduck on 2007-06-17
> **yme said:**
> However, now I play around a bit I get the error message:

Error: dev/sda1 is not a directory

It is mounted as dev/sda1, is it not?

yme

/dev/sda1 is the partition itself. In Linux erything is seen as files, even hardware. You can't access disk devices directly, you need to mount them somewhere first. In your case /dev/sda1 is mounted at /, as it's your root partition, so you are already accessing the partition ;)

---

### Post by Gimpy_Rob on 2007-06-17
> Thanks. Everything seems to be OK although there is one small partition matching the size of swap which Ubuntu seems to have added during the default install, I don't know why.

This is actually a neat way of doing things.  Logical disk partitioning allows for 4 base partitions.  The first is allocated to your main drive.  The second is an extended partition.  This can hold other partitions. SDA5 is the first partition inside SDA2.  Just leaves lots of room to expand and make linux get along better with whatever else might be on the drives.

I think that's why they do it at least.

---

