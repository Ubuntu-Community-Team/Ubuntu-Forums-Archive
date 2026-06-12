---
title: "How to dual boot with windows and ubuntu"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by benbuleong on 2006-11-07
Hi,

I am having some trouble with installing ubuntu. Initially i was dual-booting with XP and SuSE, but it turned out that SuSE is not well-supported by my laptop. I am now turning to ubuntu.

However, i am not sure how to proceed at this pt when i was doing the installation. Mainly, i want to keep GRUB (so that i can dual-boot), leave my windows XP untouched and install ubuntu on my harddisk.

The problem is how to partition my HD to achieve these things.

I have the following configuration in my HD :


[COLOR="Blue"]Partition   Filesystem      Size      Used   Unused    Flags
==============================================================
/dev/hda1    fat32        29.29GB   11.13GB  18.17GB  boot, lba
/dev/hda2    extended     45.04GB    ----     -----    lba
 /dev/hda5   fat32        19.53GB    9.29GB   10.24GB
 /dev/hda6   ext3         101.94MB   13.96MB  87.98MB
 /dev/hda7   unknown      25.41GB     ------  ------   lvm
unallocated unallocated   196.11MB    ------ -------[/COLOR]

I have windows XP on C: and D: drive, 30 GB and 20GB respectively. My SuSE was on hda7, i suppose ?

I am told to create a root partition "/" of at least 2GB and a swap partition of at least 256MB.

Any help would be appreicated.

Rgds,
Ben

---

### Post by foxmulder on 2006-11-07
I need some help too: I have 3 harddisc and want to use Edgy (server) with LVM but there is no how-to for 6.10 on LVM...

---

### Post by bobmct on 2006-11-07
I'll take a stab at this!

When you are doing the install of ubuntu the install process usually provide a partitioning suggestion.  I would recommend selecting the defaults or the one that states "use all available free space" or "take over linux partition".  That should do it and retain grub for you including the original Windoze bootable partition.  However, the appearance of the grub menu might be different because SUSE's is nice and slick and ubuntu's is just utilitarian.

Good luck.

bobmct

---

