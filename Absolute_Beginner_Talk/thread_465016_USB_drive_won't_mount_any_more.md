---
title: "USB drive won't mount any more"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by halfB on 2007-06-05
I have a seagate 120gb external drive in fat32.  It no longer mounts with upgrade to feisty.  
I have 2 questions:
How can I mount it now and how can I get it to automount in the future???
I have tried the automatix option to read/write ntfs and fat32 and then deleted the automatix option. Not recognized either way.

Here is my fdisk -l

oslo@oslo-laptop:~$ sudo fdisk -l

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        8930    71730193+   7  HPFS/NTFS
/dev/hda2            8931       10017     8731327+  83  Linux
/dev/hda3           10018       10082      522112+  82  Linux swap / Solaris
/dev/hda4           10083       12161    16699567+  83  Linux

Disk /dev/sda: 1031 MB, 1031798272 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         126     1007584    e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 50)

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    c  W95 FAT32 (LBA)


THANKS
halfB

---

### Post by aeiah on 2007-06-05
ive had the odd problem with my 1gb usb stick, although with that i could easily just reformat it.

open up gparted and see if the drive looks how it should, the filesystem may have become corrupted in some way (dont worry, it may not mean data loss). does it work in windows still?

---

### Post by Salarzae on 2007-06-05
I've something similar problem, if someone can help me out on that. I've iOmega 80GB external USB Drive. I can see it in the lsusb and through the fdisk.

=====================================================

[B][COLOR="Blue"]LSUSB OUTPUT

Bus 005 Device 003: ID 059b:007d Iomega Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  [/COLOR][/B]



=====================================================

[COLOR="SeaGreen"][B]FDISK OUTPUT

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2   *          13        2951    23607517+   7  HPFS/NTFS
/dev/sda3            2952       11769    70830585    f  W95 Ext'd (LBA)
/dev/sda4           11770       12161     3148740    c  W95 FAT32 (LBA)
/dev/sda5            2952        5891    23615518+   7  HPFS/NTFS
/dev/sda6            5892        8831    23615518+   7  HPFS/NTFS
/dev/sda7           10464       10476      104391   83  Linux
/dev/sda8           10477       11769    10385991   8e  Linux LVM
/dev/sda9            8855       10202    10827778+  83  Linux
/dev/sda10          10203       10463     2096451   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS
[/B][/COLOR]
====================================================

[COLOR="DarkOrange"][B]DMESG OUTPUT

[17180185.728000] NTFS-fs error (device sdb1): ntfs_end_buffer_async_read(): Buffer I/O error, logical block 0x600008.
[17180185.728000] NTFS-fs error (device sdb1): ntfs_end_buffer_async_read(): Buffer I/O error, logical block 0x600009.
[17180185.728000] NTFS-fs error (device sdb1): ntfs_end_buffer_async_read(): Buffer I/O error, logical block 0x60000a.
[17180185.728000] NTFS-fs error (device sdb1): ntfs_end_buffer_async_read(): Buffer I/O error, logical block 0x60000b.
[17180185.728000] NTFS-fs error (device sdb1): ntfs_end_buffer_async_read(): Buffer I/O error, logical block 0x60000c.
[17180185.728000] NTFS-fs error (device sdb1): ntfs_end_buffer_async_read(): Buffer I/O error, logical block 0x60000d.
[17180185.728000] NTFS-fs error (device sdb1): ntfs_end_buffer_async_read(): Buffer I/O error, logical block 0x60000e.
[17180185.728000] NTFS-fs error (device sdb1): ntfs_end_buffer_async_read(): Buffer I/O error, logical block 0x60000f.
[17180192.436000] sd 2:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[17180192.436000]     Additional sense: Logical unit not ready, cause not reportable
[17180192.436000] end_request: I/O error, dev sdb, sector 6291527
[17180192.436000] NTFS-fs error (device sdb1): ntfs_end_buffer_async_read(): Buffer I/O error, logical block 0x600008.
[17180192.436000] NTFS-fs error (device sdb1): ntfs_end_buffer_async_read(): Buffer I/O error, logical block 0x600009.
[17180192.436000] NTFS-fs error (device sdb1): ntfs_end_buffer_async_read(): Buffer I/O error, logical block 0x60000a.
[/B][/COLOR]
==========================================================

**Any suggestions?**

---

### Post by pimpaulogy on 2007-06-05
I am getting the same issue with my 2 gig thumb drive (Fat32) and my 4 gig Ipod Mini (Fat32).

I was getting this problem with both my laptop and desktop.  I think I resolved the laptop issue when I removed the NTFS mount option from Automatix2, but it's ultimately hard to tell at this point because I don't plug my Ipod or thumb drive into my laptop that often, not to mention I power it down at least once a day.  With my desktop, I rarely power it down and plug/unplug my Ipod at least once a day.  Ever since I updated to Feisty, it's been hit and miss whether the Ipod will mount or not.  I can plug it in - unplug it - plug it in - unplug it - plug it in and then it will mount (sometimes) and others, it plugs in the first time.  Also rebooting sometimes allows it to work right away and other times it doesn't.

My 2 cents.

---

### Post by halfB on 2007-06-05
I did not have the automatix ntfs mount option initialy installed.  Subsequently I installed then uninstalled it just in the hope.... Nothing....

My thumb drive and ipod work just fine.

HalfB

---

### Post by Ek0nomik on 2007-06-05
If you want a device to automount, then you need to edit your /etc/fstab file.  There are a lot of tutorials on this forum and other wiki/guides.

I am at work so I can't get to the other sites right now to give you a direct link, but it is easy enough to find.

```
gksudo gedit /etc/fstab
```

Then you will add your device (something like /dev/sda1, or dev/sdcc) and a mount point.

For an example, if I wanted my external HD to mount to /media/MyStuff every boot, I would:

```
sudo mkdir /media/MyStuff
```

Then in my fstab file, I would add:

```
/dev/sdc1 /media/MyStuff xxxxxxxxxxxx
```

Where xxxxxxx depends on the file system (fat32 or NTFS)

---

### Post by Ek0nomik on 2007-06-05
You **don't need** **automatix** to get NTFS write support and for it to automount.

Automatix always causes more harm than good.

If you need NTFS write support:

```
sudo aptitude install ntfs-3g
```

---

### Post by halfB on 2007-06-05
Well, I kind of think that the external drive is already being mounted somehow.
I did a MOUNT in terminal and got the following:

oslo@oslo-laptop:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hda4 on /home type ext3 (rw)
/dev/hda1 on /media/hda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)


The last line which lists /dev/sdb1 on /media/disk.....  is the external drive I do not see in my places or on my desktop.  
Does this mean it is being mounted and if so where or how??  I am getting confused.
HalfB

---

### Post by Ek0nomik on 2007-06-05
> **halfB said:**
> Well, I kind of think that the external drive is already being mounted somehow.
I did a MOUNT in terminal and got the following:

oslo@oslo-laptop:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hda4 on /home type ext3 (rw)
/dev/hda1 on /media/hda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)


The last line which lists /dev/sdb1 on /media/disk.....  is the external drive I do not see in my places or on my desktop.  
Does this mean it is being mounted and if so where or how??  I am getting confused.
HalfB

Check /media

---

### Post by halfB on 2007-06-05
Thanks Ek0 and sorry that I am not sure how to "check /media"
halfB

---

### Post by vanadium on 2007-06-05
Browse to the media directory using Nautilus. You shoudl see the directory where your drive is mounted there and then be able to navigate in it if all is well. Command line:

ls /media

to list the contents of /media

ls /media/mydrive

to list the contents of your drive.

---

### Post by halfB on 2007-06-05
Ok Ek0nomik
I found media
Here are the files I found:

cdrom 
floppy0
disk
hda1
sda1
sdb2

No sdb1?????
disk is a usb flash drive
sdb2 is empty and is less tha 3gb: not the 120gb drive that I have
HalfB
I am

---

### Post by halfB on 2007-06-05
Vanadium
(i have an bread knife from the 1950s which says vanadium on the side; hmm it has served my family well for a very long time;;;thanks)

I do no have a /media/mydrive folder.
I did not make one today.  I was worried that my external drive was already being mounted but that I could not find it.  Now I do not understand why I have an sdb2 folder in my media folder but no sdb1

HalfB

---

### Post by Ek0nomik on 2007-06-05
Is your external drive a FAT32 Western Digital?  That's what your fdisk -l shows as being sdb1.

---

### Post by halfB on 2007-06-05
It is a fat32 seagate.
Here is the fdisk-l

oslo@oslo-laptop:~$ fdisk -l 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    c  W95 FAT32 (LBA)


But now I am even more confused.  The drive was sdb1 just a bit ago.  I did remove the usb flash drive and have plugged/unplugged the 120gb drive.  Suspect that shifted it to sda1.
No Western Digital drives.

---

### Post by Salarzae on 2007-06-06
Longing for more answers :(

---

### Post by halfB on 2007-06-06
I am going to backup my usb drive then will reformat it to ext3.  From what I read, the ext3 formatted drives do not have this problem with automount recognition.  
Thanks all for your help. 
HalfB

---

