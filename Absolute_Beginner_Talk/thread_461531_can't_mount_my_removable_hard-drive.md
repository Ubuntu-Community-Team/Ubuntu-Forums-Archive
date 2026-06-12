---
title: "can't mount my removable hard-drive"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by dragon2611 on 2007-06-01
I have a 60gb 2.5" sata drive in a caddy that can be either USB2 or E-sata  but can also has a dock which fits into a 3.5" bay.

(its one of these,  

For some reason i'm unable to mount when docked ([http://www.raidsonic.de/en/pages/news/product_news.php?PHPSESSID=5583506e9f0b610d16290e2280af6bbb](http://www.raidsonic.de/en/pages/news/product_news.php?PHPSESSID=5583506e9f0b610d16290e2280af6bbb))

Its connected a pci-E sata2 controller (silicon image) and formatted NTFS.

Now i know ubuntu can talk to the Controller card ok  because it can read from the other HDD on that card perfectly fine.. (which is also NTFS)

the message it gives me when i click on the drives icon is

"Unable to mount volume shuttledisk"
then when i click on detials.

"[mntent]: line 8 in /etc/fstab is bad"
"mount: can't find /media/EFI in /etc/fstab or /etc/mtab"

Wander ifs seeing an EFI partition table? there may still be one on the hard-drive in the caddy was originally from my macbook left over from a hdd upgrade.

Any ideas what to do, it would be nice if i could get it show up in Ubuntu.

Im running ubuntu 7.04 32bit on a althon 64 x2 3800+

---

### Post by taurus on 2007-06-01
Can you post the output of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by dragon2611 on 2007-06-02
> **taurus said:**
> Can you post the output of these two commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

Would be happy to ;)

```
dragon@Dragon-dtop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9040    72610816    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9725    78116031    7  HPFS/NTFS

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24792   199141708+   5  Extended
/dev/sdc5            2573       24792   178482118+   7  HPFS/NTFS
/dev/sdc6               1         124      995935+  82  Linux swap / Solaris
/dev/sdc7             125        2572    19663528+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        7296    58602496    7  HPFS/NTFS

Disk /dev/sde: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       19929   160079661    7  HPFS/NTFS

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc7
UUID=7b933d6a-04de-4a8d-a496-9a452f59c4dc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdd1
UUID=3E3ECB7B3ECB2B2B /media/EFI      system  partition       vfat    defaults,utf8,umask=007,gid=46 0 1
# /dev/sda1
UUID=C658C83358C82451 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=7200A03D00A009E5 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdc5
UUID=A6A4631D96FDDF5C /media/sdc5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sde1
UUID=983867D63867B244 /media/sde1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdc6
UUID=abaace33-1067-4aae-b6e6-0f59ed53bd22 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

---

### Post by Inxsible on 2007-06-02
> # /dev/sdd1
UUID=3E3ECB7B3ECB2B2B /media/EFI      system  partition       vfat    defaults,utf8,umask=007,gid=46 0 1

Its being read as a system partition...could that be a problem ?

you said it was supposed to be NTFS correct ?
But it says vfat = FAT32

---

### Post by dragon2611 on 2007-06-03
> **Inxsible said:**
> Its being read as a system partition...could that be a problem ?

you said it was supposed to be NTFS correct ?
But it says vfat = FAT32

its supposed to be NTFS, i only formatted it when i took it out of the macbook, so is it possible that the old EFI partition table is still intact as the pc probably only updated the MBR partition table..


although the fdisk command lists it as NTFS

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        7296    58602496    7  HPFS/NTFS

---

### Post by pappapump on 2007-06-03
If you have the ability to mount it as a usb drive, you should try that first to see if it has a different reading.
Then if it still says it's a fat volume you do a complete format with any ntfs based system to change it.

---

### Post by dragon2611 on 2007-06-03
> **pappapump said:**
> If you have the ability to mount it as a usb drive, you should try that first to see if it has a different reading.
Then if it still says it's a fat volume you do a complete format with any ntfs based system to change it.

It brings up the same error on USB.

Although It shows up in windows and osx on my mac ok 

Got an old p2 333mhz laptop (128mb ram, usb1.1) laying around that i recently got around to installing an OS back onto and setting it up for webbrowsing.etc

Thought i'd plug the drive into the USB on that and low and behold it Mouted the drive 

Heres the real kicker, its running ubuntu 7.04 !

Main difference between the installs is the live cd Doesn't boot on that laptop so i installed from the alternative cd.  Both are running ubuntu 7.04 32bit though.

So why does it mount fine on one machine but not on the other?

---

