---
title: "mounting new hard drive"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by seanmbarrett on 2007-02-18
hi 
i have a second harddrive with all my files i would like to mount. it is in fat 32. can someone walk me though the process. thanks

---

### Post by annda on 2007-02-18
try this:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

if you have problems, ask again.

---

### Post by STREETURCHINE on 2007-02-18
give us a out put of your fstab


```
sudo fdisk -l
```

---

### Post by seanmbarrett on 2007-02-18
Disk /dev/hda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4776    38363188+  83  Linux
/dev/hda2            4777        4982     1654695    5  Extended
/dev/hda5            4777        4982     1654663+  82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36481   293033601    c  W95 FAT32 (LBA)
seanmbarrett@sean-desktop:~$

---

### Post by annda on 2007-02-18
you will need to add the following line to your fstab:

/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0

(assuming you want to mount your drive under /fat_files as in aysiu's tutorial. you may want to mount in in the media folder like other partitions. make a mount point of your choice,  like /media/my_drive_name using the following command: sudo mkdir /media/my_drive_name and change the name in fstab to whatever you like)

you can do that by running from the terminal

```
gksudo gedit /etc/fstab
```

copy and paste that line and reboot - voila!

---

### Post by STREETURCHINE on 2007-02-18
[oops double post

---

### Post by STREETURCHINE on 2007-02-18
```
gksudo gedit /etc/fstab
```

and add this line at the end

```
/dev/hdb1 /media/hdb1 vfat iocharset=utf8,umask=000 0 0
```

save then make a mount point

```
sudo mkdir /media/hdb1 
sudo umount /dev/hdb1
sudo mount -a 
df -h
```

---

### Post by ellis rowell on 2007-02-18
I had no problem adding a second drive to my system. I obtained an external drive case which plugs into the USB2 port. The disk has three partitions and it mounted automatically. I also have a wireless router which the computer (running Edgy) found and connected automatically as well. The computer is an Acer Aspire T120 and works faster under Edgy than under Windoze XP. The main disk is only 10.2GB (the Windows disk is 80GB, which I still keep to plug in for checking information on logins etc). Because the hard disk is formatted Fat32 under Windoze it is readable by both systems.

---

### Post by seanmbarrett on 2007-02-18
hi again it says this "[mntent]: line 1 in /etc/fstab is bad"   when i type in mount -a
i tried some thing earlier . here is my fstab
/dev/hdb1   /media/hdb1 vfat   iocharset=utf8,umask=000   0   0/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8dd5ab25-b263-4420-b3df-2352a6700895 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=3d4c7024-f4a3-4357-901e-cfb0a94849fa none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

hope someone can help thanks sean

---

### Post by STREETURCHINE on 2007-02-18
ok make this line 
/dev/hdb1 /media/hdb1 vfat iocharset=utf8,umask=000 0 0/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0# /etc/fstab: static file system information.

look like this

/dev/hdb1 /media/hdb1 vfat iocharset=utf8,umask=000 0 0

and start again

---

### Post by seanmbarrett on 2007-02-18
street urchine,
   thanks it worked!!!! much better. thanks for the help and everyone else who helped also. sean

---

