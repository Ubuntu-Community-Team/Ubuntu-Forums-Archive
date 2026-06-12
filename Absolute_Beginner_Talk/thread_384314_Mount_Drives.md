---
title: "Mount Drives"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by phelixnyc on 2007-03-14
I just realized that automatix2 comes with app that will mount local drives FAT32 & NTFS and allows you to read and write to them. I have to more hdd's both NTFS with files I would like to access from ubuntu , I am still new to ubuntu, and was wondering if this is safe?

---

### Post by taurus on 2007-03-14
Post the outputs of these two commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by phelixnyc on 2007-03-14
This is what I get

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1           11983       14593    20972857+  83  Linux
/dev/hda2           11722       11982     2096482+  82  Linux swap / Solaris
/dev/hda3               1       11721    94148901   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

---

### Post by taurus on 2007-03-14
And which one have you mounted so far and which one do you want to mount now, /dev/hdb1 or /dev/sda1?

---

### Post by phelixnyc on 2007-03-14
I want to mount /dev/hdb1.

---

### Post by taurus on 2007-03-14
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by phelixnyc on 2007-03-14
Thanx.

---

### Post by nickolas1386 on 2007-03-14
I have mounted the drive hda1 which is my windows partition. It only opens in read mode. How do i change it so that the permissions for all users is read and write?

This is my fstab configuration
Ubuntu 6

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=f8068d43-07b1-409f-b31e-aaa7b19c20ce /               ext3    defaults,errors=remount-ro 0       1
#/dev/hda1
#UUID=8440E5FE40E5F738 /media/hda1     ntfs    #defaults,nls=utf8,umask=055,gid=46 0       1
UUID=8440E5FE40E5F738 /media/hda1 ntfs nls=utf8,umask=0000 0 0
# /dev/hda3
UUID=981c0e97-5b94-4b1a-ac94-368f16b7705d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by taurus on 2007-03-14
> **nickolas1386 said:**
> I have mounted the drive hda1 which is my windows partition. It only opens in read mode. How do i change it so that the permissions for all users is read and write?

This is my fstab configuration
Ubuntu 6

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=f8068d43-07b1-409f-b31e-aaa7b19c20ce /               ext3    defaults,errors=remount-ro 0       1
#/dev/hda1
#UUID=8440E5FE40E5F738 /media/hda1     ntfs    #defaults,nls=utf8,umask=055,gid=46 0       1
UUID=8440E5FE40E5F738 /media/hda1 **ntfs** nls=utf8,umask=0000 0 0
# /dev/hda3
UUID=981c0e97-5b94-4b1a-ac94-368f16b7705d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

You cannot write to ntfs filesystem with ntfs driver.  You need to install ntfs-3g if you want to write to it.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by nickolas1386 on 2007-03-15
Thank You Very much i followed steps on that guide and am now a happy newbie.

---

### Post by lwalper on 2007-03-16
So, when I run  'sudo fdisk -l' I get the following:

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3987    32025546    7  HPFS/NTFS
/dev/hda2            3988        9762    46387687+  83  Linux
/dev/hda3            9763       10011     2000092+   5  Extended
/dev/hda5            9763       10011     2000061   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1023     8217243   54  OnTrackDM6

Disk /dev/sda: 257 MB, 257949696 bytes
16 heads, 32 sectors/track, 984 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         983      251632    6  FAT16

**********************************
To mount the NTFS partition I should add the line:
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0

And for the FAT32 partition I should add the line:
/dev/sda   /media/sda1   fat32   nls=utf8,umask=0222   0   0

??

and then create mount points for each?

---

