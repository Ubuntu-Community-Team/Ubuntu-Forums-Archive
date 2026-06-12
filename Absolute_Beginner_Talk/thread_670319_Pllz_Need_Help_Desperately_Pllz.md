---
title: "Pllz Need Help Desperately Pllz"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by coolnik6 on 2008-01-17
i installed ubuntu 
on my hard disk which already has windows xp
 
I HAVE 2 PARTIOTNS C: AND D:  EACH 12 BG AND 45 GB RESPECTIVELY
I INSTALLEDS USING 1ST OPTION WHERE IT RESIZES THE PARTION SOMETIHNG LIKE THAT

DURING FINAL INSTALLATION IT SAID HDA3  AND HDA 6 WILL BE FORMATTED 
I WENT ON
UBUNTU GOT INSTALLED
WHEN I RESTARTED  N LOGGED IN XP I WAS NOT ABLE TO ACCESS MY D: DRIVE 
IT SAID ITS NOT FORMATTED  N FORMAT IT NOW?
I GOT SCARED
I MEAN I HAVE MY ALL IMP DATA ON D: DRIVE
I FEEL ITS STILL THERE ALONG WITH UBUNTU SYSTEM
IM POSTING A THE RESULTS OF FDISK -L COMMAND IT SHOEWED ME THIS
I WNAT MY DATA BACK
MY D/: DRIVE  WAS 33GB FULL OUT OF 45 GB N IT WAS NTFS
I HAD MY WINDOWS SYSTEM ON C: ITS SIZE IS 12 GB SOMETHING
PLZZ HELP I WANT MY DATA BACK
PLZ UBUNTU PPL HELP ME

---

### Post by coolnik6 on 2008-01-17
Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23655    11922088+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/hda2           23668      104375    40676580+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda3          104375      119149     7446127+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda5           23668      103674    40323150    7  HPFS/NTFS
/dev/hda6          103674      104375      353398+  82  Linux swap / Solaris

---

### Post by Sef on 2008-01-17
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").  It can recover your partitions.

---

### Post by erginemr on 2008-01-18
I know that this will not be a direct solution to your problem, or any kind of solution for that matter. But you might at least be able to mount your windows drives from within Ubuntu (also the missing D:\ drive, which is being reported as raw data) and access the files inside. Unfortunately, this will be a looong post but anyway...

As a reminder, here is the output of your "sudo fdisk -l" command:
> **coolnik6 said:**
> Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23655    11922088+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/hda2           23668      104375    40676580+   f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda3          104375      119149     7446127+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda5           23668      103674    40323150    7  HPFS/NTFS
/dev/hda6          103674      104375      353398+  82  Linux swap / Solaris
nik@nik-desktop:~$

and here is the contents of your "/etc/fstab" file:
> **coolnik6 said:**
> i have posted the fstab file in etc directory

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=a1b67225-62e5-41f2-a858-46e076380009 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=da3dc3e2-64ce-481f-a4ed-28b3d57460fa none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto

As a comparison, here is a standard /etc/fstab file with lines for auto-mounting an ntfs drive and a vfat (fat32) drive:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=2cd4fd47-f5e2-4512-92c9-fb402e3a214e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda8
UUID=c0b2f548-e488-49cf-9f29-2714f455b3a8 /home           ext3    defaults        0       2
# /dev/hda1
UUID=60E0E51CE0E4F8E4 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=D8D3-0820  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=66700d1c-d4e9-4f39-ab0f-a1191794251d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

Normally, the line mounting ntfs used to be:
```
/dev/hda1 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
```
and the line mounting fat32 used to be:
```
# /dev/hda5
UUID=D8D3-0820  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
```

But as a result of the recent developments in Linux, the use of UUID, a new way to identify hard drives has been gaining more ground in recent distros. So, the parts
```
# /dev/hda1
# /dev/hda5
```
have been commented out by Ubuntu installer and the UUID of the corresponding hard drives have been implemented instead:
```
UUID=60E0E51CE0E4F8E4 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=D8D3-0820  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
```
You can obtain the UUID's for your ntfs and fat32 hard drives with either:
```
sudo blkid
```
or
```
sudo vol_id -u /dev/hda1
sudo vol_id -u /dev/hda2
sudo vol_id -u /dev/hda5
```

From the outcome of "sudo fdisk -l", it appears that your fat32 partitions are located in "dev/hda1" and "/dev/hda2", and your ntfs partition is located in "/dev/hda5". Speaking of which, this also means that you only have one hard drive, though divided into two by Windows as C:\ and D:\.

Hence, in your case, you should add the following lines to your /etc/fstab file:

```

UUID=................ /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
UUID=................ /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
UUID=................ /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
```

Make sure that /media/hda1, hda2 and hda5 as a directory pre-exist in your file system and use the result of one of the above two commands to insert UUID of /dev/hdaX. Reboot and see if there is any  improvement.

But the error message as a result of "sudo fdisk -l" is ominous enough: "Partition 1 does not end on cylinder boundary."
And as far as I know, points to a problem in your partition table. In this respect, I suggest you to sef's advice above, first.

---

