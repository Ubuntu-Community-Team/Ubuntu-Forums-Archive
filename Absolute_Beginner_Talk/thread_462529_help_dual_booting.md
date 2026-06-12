---
title: "help dual booting"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by lilmill on 2007-06-02
I found this google video on setting xp dual boot so I figured i'd try linux it showed t odo it in this order.
1. partition disk. ( I split a 30 into 2 15's)
2 install winblows on to first partition hda
3.install linux on to second partitions ( Isplit the remainder into 1gig swap and 14 gigs /)
4.reboot system and you should see a os boot loader(grub??) and you can choose winblows if you want.
so heres the problem The Install seemed smooth but I dont get the boot loader it goes straight to ubuntu with no options of xp. I need xp because I have a drive mapped as a backup for the main computer running vista

---

### Post by Inxsible on 2007-06-02
> **lilmill said:**
> I found this google video on setting xp dual boot so I figured i'd try linux it showed t odo it in this order.
1. partition disk. ( I split a 30 into 2 15's)
2 install winblows on to first partition hda
3.install linux on to second partitions ( Isplit the remainder into 1gig swap and 14 gigs /)
4.reboot system and you should see a os boot loader(grub??) and you can choose winblows if you want.
so heres the problem The Install seemed smooth but I dont get the boot loader it goes straight to ubuntu with no options of xp. I need xp because I have a drive mapped as a backup for the main computer running vista

Did you by any chance install ubuntu over XP ??

can you post the ouput of the following commands:
```
sudo fdisk -l
```
-l is lowecase L
```
gedit /etc/fstab
```

---

### Post by jonward0690 on 2007-06-02
So your computer does not go to the grub menu at all was you shure to install grub even though grub should be installed by default.

---

### Post by Bernie01 on 2007-06-02
I have this problem in reverse. Windows XP still boots but there is no sign of Ubuntu on boot up

---

### Post by confused57 on 2007-06-02
> **lilmill said:**
> I found this google video on setting xp dual boot so I figured i'd try linux it showed t odo it in this order.
1. partition disk. ( I split a 30 into 2 15's)
2 install winblows on to first partition hda
3.install linux on to second partitions ( Isplit the remainder into 1gig swap and 14 gigs /)
4.reboot system and you should see a os boot loader(grub??) and you can choose winblows if you want.
so heres the problem The Install seemed smooth but I dont get the boot loader it goes straight to ubuntu with no options of xp. I need xp because I have a drive mapped as a backup for the main computer running vista

Do you see a prompt when your pc boots up to press "Esc" to enter grub?

---

### Post by confused57 on 2007-06-02
> **Bernie01 said:**
> I have this problem in reverse. Windows XP still boots but there is no sign of Ubuntu on boot up

Boot the live cd, open a terminal(Applications---Accessories---Terminal), enter & post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

---

### Post by Bernie01 on 2007-06-03
Here is the output of sudo fdisk -l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdd: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        3205    25744131    c  W95 FAT32 (LBA)
/dev/hdd2            3206        4870    13374112+   c  W95 FAT32 (LBA)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       14944    58597087+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         486     3903763+  82  Linux swap / Solaris
/dev/sdb2             487         996     4096575    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

I hope somebody can help

---

### Post by jonward0690 on 2007-06-03
Yea it just looks like you need to reinstall grub.

---

### Post by jonward0690 on 2007-06-03
Well I found some where you can go to try to reinstall grub here is the best of luck.   [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by confused57 on 2007-06-03
> **Bernie01 said:**
> Here is the output of sudo fdisk -l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdd: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        3205    25744131    c  W95 FAT32 (LBA)
/dev/hdd2            3206        4870    13374112+   c  W95 FAT32 (LBA)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       14944    58597087+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         486     3903763+  82  Linux swap / Solaris
/dev/sdb2             487         996     4096575    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

I hope somebody can help

It's possible that grub was installed to the mbr of hdd, if you're not already booting first to this drive, try it and see.
If you don't get a grub menu, you can mount your Ubuntu root partition with the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
except to mount you would use:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda2 /media/ubuntu
gedit /media/ubuntu/boot/grub/menu.lst
gedit /media/ubuntu/boot/grub/device.map
```

The live cd can also be used to reinstall grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If you're not able to boot Ubuntu from hdd, then post your menu.lst & device.map files.

---

