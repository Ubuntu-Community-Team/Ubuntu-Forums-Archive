---
title: "[SOLVED] Partitionig for Windows XP/Ubuntu dual boot"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by getitright on 2008-04-16
I am considering installing Ubuntu to dual boot with Windows XP (XP pre-installed ). Having investigated the HD partitioning options I would like to end up with the following scenario for the partititions:

Windows XP (NTFS)

Ubuntu/Home-shared data ( using FS-Drive application to access files from Windows)

Ubuntu/(ext3)

/swap

1. Can I do this? and

2. If I can, how do I bring about the desired outcome?

---

### Post by Inxsible on 2008-04-16
Check out these links which help you paritition and install ubuntu

[partitioning]("http://www.psychocats.net/ubuntu/partitioning")   [installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by TWO on 2008-04-16
> **getitright said:**
> I am considering installing Ubuntu to dual boot with Windows XP (XP pre-installed ). Having investigated the HD partitioning options I would like to end up with the following scenario for the partititions:

Windows XP (NTFS)

Ubuntu/Home-shared data ( using FS-Drive application to access files from Windows)

Ubuntu/(ext3)

/swap

1. Can I do this? and

2. If I can, how do I bring about the desired outcome?

[https://help.ubuntu.com/community/WindowsDualBoot#head-1529b642af35c3793374b3b01cbbc41d0ca2efb1](https://help.ubuntu.com/community/WindowsDualBoot#head-1529b642af35c3793374b3b01cbbc41d0ca2efb1)

This page might help in setting up a dual boot.

!) Yes, I think it's possible to do so. I have a dual boot set up myself between WinXP and Kubuntu.
I have four partitions as well: one for WinXP, a shared FAT 32 partition, Kubuntu and Swap. 

2) Am I right in assuming that you already have Windows installed? Does it take up the whole drive? If so, then you will have to resize the partition using a repartitioning program such as QtParted which I think comes on the Ubuntu Live CD. Make sure you back up your data before you play about with the partitions though. Anyway, as far as setting up partitions go, it is easily done during the installation process for Ubutnu. Just make sure you select the 'manual' option for editing the tables.

---

### Post by Paqman on 2008-04-16
> **getitright said:**
> 
1. Can I do this? and

2. If I can, how do I bring about the desired outcome?

Absolutely.

First, BACK UP any important data in Windows just to be safe. 

During Ubuntu installation choose "manual partitioning". You'll be presented with the Gparted partitioning tool. Shrink your Windows partition down, creating free space. This can take quite a while. From that free space you want to create your three new partitions, and assign the mount points to them (for /home and / anyway) 

Root (/) will need about 10GB+, swap about 1.5x your RAM, and /home can be as big as you like. 

Don't sweat about making it perfect, you can always change it later using Gparted.

---

### Post by saxuntu on 2008-04-16
Another piece of the puzzle is to defragment windows before you touch anything! then resize, create and install. I also recommend using the LiveCD (gparted is under system->admin) to resize and create partitions before using the install function. You'll still need to do a manual install but you won't be partitioning and only reformatting your root partition because its required.

---

### Post by mbadawi23 on 2008-04-16
> **saxuntu said:**
> Another piece of the puzzle is to defragment windows before you touch anything! then resize, create and install. I also recommend using the LiveCD (gparted is under system->admin) to resize and create partitions before using the install function. You'll still need to do a manual install but you won't be partitioning and only reformatting your root partition because its required.

I second that thought... While resizing your partitions you want to do it as cleanly as possible.

Also I second the post suggesting to BACKUP FIRST!

have fun.

---

### Post by getitright on 2008-04-16
Yes I do have Windows XP installed.

My HD is formatted for NTFS. My aim was to avoid having a FAT 32 partition by making the /home Ext 3.

---

### Post by spaceworm on 2008-04-16
my acer M1100 came with a sata drive with a fat partition with vista plus a ntfs partition meant for storage, I guess. I don't like vista for my games, it's slow, so I tried to install xp, but it won't load, it won't get past the first stage where it copies system files and will get back to the start of installation.

so I installed ubuntu instead, and it installed fine. but I didn't know how to split the hard drive in two so I made it automatic partitioning so ubuntu took all of the hard drive (320 Gb)

so now I want to resize the ext3 partition so that I can install some xp ntfs partitions in the other half of the drive...

but in gparted the options for resizing/moving are grayed out!!! So it won't let me resize at all :(

Does anyone know why this is happening? Does it have to do with root user not being allowed directly? I like ubuntu but I don't know how to move around in it yet.

Thanx.

---

### Post by ConsumingFire783 on 2008-04-16
You don't necessarily need the FAT32 drive.  New distros of Ubuntu have read/write capabilities in NTFS, so you can easily access files from it without the need for a FAT32 swap partition.  To get to anything in linux, you can install a program called Linux Reader in windows, which will allow you access to anything on the ext3 linux partition.

---

### Post by getitright on 2008-04-17
Thanks. There is enough here to get me started.

One further question. My HD has a capacity of 300Gbs, I was thinking of allocating 30Gbs for Windows, 15Gbs for Ubuntu, 3Gbs for Swap and the remainder for /home ext3. Do these patitions seem reasonable?

---

