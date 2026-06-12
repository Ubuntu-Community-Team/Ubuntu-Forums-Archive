---
title: "Can someone convert these instuctions into plain english please"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by Eric Plumrose on 2005-10-08
Hi Everyone.

I have an Sata hard drive controler that Ubuntu can not see. 

I have been onto the SIS website and downloaded the driver for the controler chip on my motherboard. 

However I can not understand the readme file. Could someone please translate this into plain english.

1. Files List
   - Makefile
   - sata_sis.c

   Since the ata_host_set structure is redefined from kernel-2.6.10,
   I have to part the sata_sis.c to different branch.

2. How to build the driver ?
   1. You have to prepare the kernel source. Downlad it / Untar it / and link it to /usr/src/linux
   2. Check you kernel version. Take 2.6.10 for an example, cd sis18x_2.6.10_1.00.00
   2. Change to administrator.
   3. Type " make " to build the driver
   4. Type " make install " to intall the sata_sis.ko module

3. How to use it ?
   1. To load the driver, use " modprobe sata_sis ". Or "load-18x"
   2. To unload the driver, type " rmmod sata_sis ". Or "unload-18x"
   3. For SATA devices will be named to /dev/sda, /dev/sdb, /dev/sdc etc,.
   4. For S-ATAPI devices will be named  to /dev/scd0, /dev/scd1, /dev/scd2, etc,.

4. Partion the disk
   If you disk does not have any partition, you have to create some first.
  	fdisk /dev/sd[a-d]

5. Mount the partition to somewhere
   After you get some partitions, mount it to somewhere to use.
   like, mount /dev/sda1 /mnt/dos  ....

6. Summary of Current Status
   1. Fedore Core-3 use kernel 2.6.9, at this release does not support S-ATAPI devices
   2. From kernel 2.6.10, libata port support S-ATAPI devices.
   3. MSI ODD device, model MS-8452T could not pass the identify command.


I am running Kubuntu 5.04 (I have tried Breezy and it can not find the SATA drives)

Thanks a lot in advance.

Eric.

---

### Post by Kyral on 2005-10-08
the sata_sis driver should already be there.

try sudo modprobe sata_sis

then add it to your /etc/modules

---

### Post by Eric Plumrose on 2005-10-09
I typed "sudo modprobe sata_sis" into a terminal and didn't get a error just a command prompt.
It didn't seem to do anything.

How do you add it to /etc/modules?

Thanks a lot

Eric

---

### Post by poofyhairguy on 2005-10-09
[QUOTE=Eric Plumrose]I typed "sudo modprobe sata_sis" into a terminal and didn't get a error just a command prompt.
It didn't seem to do anything.[/QUOTE]

Taht means success.

> 
How do you add it to /etc/modules?

Thanks a lot

Eric

this command:

sudo gedit /etc/modules

then add that word to the end of the file!

---

### Post by Eric Plumrose on 2005-10-09
I am still having trouble :(
 
I have added sata_sis to the bottom of /etc/modules.

I then typed in sudo fdisk -l

But I only got the data for my 2 Ide hard drives. hda and hdb.

Thanks a lot Eric

---

### Post by poofyhairguy on 2005-10-09
[QUOTE=Eric Plumrose]I am still having trouble :(
 
I have added sata_sis to the bottom of /etc/modules.

I then typed in sudo fdisk -l

But I only got the data for my 2 Ide hard drives. hda and hdb.

Thanks a lot Eric[/QUOTE]


You have to reboot for it to take effect. Reboot and then see what happens.

---

