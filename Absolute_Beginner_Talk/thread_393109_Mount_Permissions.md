---
title: "Mount Permissions"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by falk3r on 2007-03-25
Quickie - 

Help me to understand the proper mount commands for my external HDD.

Whenever I mount a drive in root, I do not have permissions as user to access it.

```
mount -t  ext3 /dev/sdb1 /media/xternal
```

Now Nautilus runs into permission errors.

And while you're at it... would the code be significantly different for FAT32?

Thank you for your time,
 - falk3r

---

### Post by taurus on 2007-03-25
```
sudo mount -t vfat **/dev/sdb1** **/media/xternal** -o iocharset=utf8,umask=000
```

---

### Post by martinw89 on 2007-03-25
Are you saying you can mount it but can't get into it?  Or are you saying that you can't mount it?  If you can't mount it, type 
```
 sudo mount -t  ext3 /dev/sdb1 /media/xternal
```The sudo before the command means it will run as root.  If the drive is FAT32, change ext3 to vfat.

Edit: taurus beat me to it.  And I forgot to add the iocharset and umask options anyway :)

---

### Post by falk3r on 2007-03-25
Sorry for the confusion, I can mount it... I just cannot get into it. I'll try Taurus's suggetsions and report back.

Thanks,
 - falk3r

---

### Post by falk3r on 2007-03-25
Trying to mount with you suggestion:

```
falk3r@falk3r-desktop:~$ sudo mount -t ext3 /dev/sdb1 /media/xternal893 -o iocharset=utf8,umask=000
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Suggestions?

Thanks,
 - falk3r

---

### Post by martinw89 on 2007-03-25
If this is your external drive I'm assuming it vfat so try
```
sudo mount -t vfat /dev/sdb1 /media/xternal893 -o iocharset=utf8,umask=000
```
The error you got is reporting that the partition you are trying to mount is not the type you specified.

Hope that helps
-Martin

---

### Post by falk3r on 2007-03-25
The problem persists:

```
falk3r@falk3r-desktop:~$ sudo mount -t vfat /dev/sdb1 /media/xternal893 -o iocharset=utf8,umask=000
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I'm pretty sure it's the ext3 format, see the following fdisk display.

```
falk3r@falk3r-desktop:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        9729    78148161   83  Linux

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30254   243015223+   7  HPFS/NTFS
/dev/sda2           30255       30515     2096482+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

```

---

### Post by falk3r on 2007-03-26
Just closing out the thread, the following commands had to be run, to create the file system:

```
sudo mkfs.ext3 /dev/sdb1
```

Then I was able to mount the drive, but be warned... that command is like formatting... any data that is on your /dev/sdb1 will be lost.

 - falk3r

---

### Post by GordSellar on 2007-04-05
> **taurus said:**
> ```
sudo mount -t vfat **/dev/sdb1** **/media/xternal** -o iocharset=utf8,umask=000
```

So, this code worked perfectly for me, and I'm wondering how I can alter my fstab to automount with exactly these permissions? Right now, my fstab isn't automounting or giving such permissions, and it looks like this:

```
/dev/sdb1   /media/usb1   vfat umask=000,utf8 0 1
```

Any help would be appreciated! Thanks!

---

