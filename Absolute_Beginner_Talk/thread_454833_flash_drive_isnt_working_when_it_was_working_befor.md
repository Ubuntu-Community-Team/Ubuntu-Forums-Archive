---
title: "flash drive isnt working when it was working before, plz help"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by bishop9226 on 2007-05-25
my kingston 2gb usb flash was working JUST FINE in ubuntu, then i was messing with automatix' program that lets you write to ntfs drives so i took it out. now it wont recognize it again.  whats wrong and how do i fix it?:(

thanks

---

### Post by arnieboy on 2007-05-25
> **bishop9226 said:**
> my kingston 2gb usb flash was working JUST FINE in ubuntu, then i was messing with automatix' program that lets you write to ntfs drives so i took it out. now it wont recognize it again.  whats wrong and how do i fix it?:(

thanks

Its not working because you probably had the flash drive plugged in when running the NTFS/FAT32 mounter option from Automatix and it got added to the root mountable device list in /etc/fstab
Please paste the results of the following command:
```
cat /etc/fstab
```

-Arnie
Automatix Team Lead

---

### Post by bishop9226 on 2007-05-25
no i followed the warning and removed it before installing that.  the mounter didnt work anyway though as it demounted everything then didnt remount anything on reboot, so i uninstalled it and all my drives came back. but my usb drive doesnt work. here you go, thx for help btw - 

--

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=5dc14a4a-f07c-41f6-b0e7-e9bdac9bcf76 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=4ECC1EF4CC1ED5D5 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=0840FC9040FC85AA /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=98A4C3ECA4C3CAC8 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=9A4807B648078FE5 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=1CC45C6DC45C4AE2 /media/sdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb6
UUID=367825067824C689 /media/sdb6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb7
UUID=3464444C64441352 /media/sdb7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda10
UUID=C6CD-B828  /share          vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=2978aab1-43b1-4062-b3fe-2bed75383bea none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by arnieboy on 2007-05-25
> **bishop9226 said:**
> no i followed the warning and removed it before installing that.  the mounter didnt work anyway though as it demounted everything then didnt remount anything on reboot, so i uninstalled it and all my drives came back. but my usb drive doesnt work. here you go, thx for help btw - 

--

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=5dc14a4a-f07c-41f6-b0e7-e9bdac9bcf76 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=4ECC1EF4CC1ED5D5 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=0840FC9040FC85AA /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=98A4C3ECA4C3CAC8 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=9A4807B648078FE5 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=1CC45C6DC45C4AE2 /media/sdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb6
UUID=367825067824C689 /media/sdb6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb7
UUID=3464444C64441352 /media/sdb7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda10
UUID=C6CD-B828  /share          vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=2978aab1-43b1-4062-b3fe-2bed75383bea none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
Is your USB drive NTFS formatted?
do the following:
```
sudo apt-get install ntfs-3g
```
and then restart your computer and check if the USB drive gets mounted or not. If it doesnt, then keep it plugged in and paste the result of the following command:
```
sudo fdisk -l
```

---

### Post by bishop9226 on 2007-05-26
that fixed it. it also fixed the problem of my cd's not auto loading on the desktop either!! THANKS

so would you mind explaining to me what went wrong?  id like to try to get automatix ntfs write working but the last 2 times i rebooted after installing it i had none of my ntfs drives mounted! ;(

---

