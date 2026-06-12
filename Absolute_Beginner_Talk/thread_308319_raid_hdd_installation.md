---
title: "raid hdd installation"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by dplewis on 2006-11-27
First time installing linux, having trouble determining what to search on.  

Today I decided to load Ubuntu Server 6.06 on an old PC.  My plan is to make the PC a file server.  The PC had 3 HDD's

-1 40GB
-2 120GB (configured in the bios for RAID 1

During the installation, I selected to erase the 40GB.  I didn't do anything for the 120GB HDD's.

How can I tell if Ubuntu recognizes the 2 120GB HDD's as one partition that is RAID 1?

When I ran fdisk -l I get the following

disk dev/sda 123.5 GB
disk dev/sda doesn't contain a vaild partition table

disk dev/sdb 123.5GB

/dev/sba1 system hpfs/ntfs

I'm not sure what all this means, can someone help decipher this text for me?

Thank you.

---

### Post by CatKiller on 2006-11-28
I've never used RAID, but the [Release Notes]("http://www.ubuntu.com/download/releasenotes/606#head-f0fc50174e566788f02aa164fb6e80aa9c65ee24") say > If you are installing from the Desktop CD on a system that already has one or more RAID arrays or LVM volume groups set up, you must disable the arrays (sudo /etc/init.d/mdadm stop; sudo mdadm --stop --scan) and volume groups (sudo vgchange -a n) before starting the installer. I don't know if that means anything to you - it doesn't to me.

---

### Post by dplewis on 2006-11-28
here's some additional information

the raid controller I'm using is "Silicon image SiI 3112 SATARaid controller"

_when I ran fdisk -l here's the output_

Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15016   120615988+   7  HPFS/NTFS

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4865    39078081    5  Extended
/dev/hda5   *           1          31      248944+  83  Linux
/dev/hda6              32        4865    38829073+  8e  Linux LVM

[U]
when I ran 'dmesg', I get the following.[/U]

[42949378.140000] scsi1 : sata_sil
[42949378.140000]   Vendor: ATA       Model: HDS722512VLSA80   Rev: V33O
[42949378.140000]   Type:   Direct-Access                      ANSI SCSI revisio                                                                             n: 05
[42949378.140000]   Vendor: ATA       Model: HDS722512VLSA80   Rev: V33O
[42949378.140000]   Type:   Direct-Access                      ANSI SCSI revisio                                                                             n: 05
[42949378.150000] Driver 'sd' needs updating - please use bus_type methods
[42949378.150000] SCSI device sda: 241254720 512-byte hdwr sectors (123522 MB)
[42949378.150000] SCSI device sda: drive cache: write back
[42949378.160000] SCSI device sda: 241254720 512-byte hdwr sectors (123522 MB)
[42949378.160000] SCSI device sda: drive cache: write back
[42949378.160000]  sda: unknown partition table
[42949378.180000] sd 0:0:0:0: Attached scsi disk sda
[42949378.180000] SCSI device sdb: 241254720 512-byte hdwr sectors (123522 MB)
[42949378.180000] SCSI device sdb: drive cache: write back
[42949378.190000] SCSI device sdb: 241254720 512-byte hdwr sectors (123522 MB)
[42949378.190000] SCSI device sdb: drive cache: write back
[42949378.190000]  sdb: sdb1

---

### Post by dplewis on 2006-11-28
I decided to install dmraid.

After installing dmraid, I ran the dmraid -s command.

this is what I got:

dplewis@arthur:~$ sudo dmraid -s
*** Active Set
name   : sil_agbheacdcgbj
size   : 241252672
stride : 0
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0

does this mean the raid is configured on my PC?

---

