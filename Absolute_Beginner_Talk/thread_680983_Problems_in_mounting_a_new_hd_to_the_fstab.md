---
title: "Problems in mounting a new hd to the fstab"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by MaximB on 2008-01-28
My friend which new to GNU/Linux and lives in another city (and doesn't speak English) has problems mounting his Hard disk to his fstab
Ubuntu's sftab is not like any other distro's fstabs, it's a bit different.
I can't see his computer, I only can give him cli commands and hope he can follow them.

So here is the deal.
He installed Ubuntu - completely new installation (no advanced mode).

#cat /etc/fstab

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=21b41332-4b58-4f7f-bbe2-9957c4f9d40e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=395536e6-8e73-4d54-bc8b-b8e91b4d1016 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
``` 

#mount :

```
ruslan@ruslan-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
**/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev)**
```

/dev/sdb1 it is the hard disk which he needs to mount (as far as I understand).

I suggested him to do :

1. sudo mkdir /disk2
/disk2 will be his new mount point for his hard disk

2. sudo gedit /etc/fstab 
and add this line at the bottom of the file :
/dev/sdb1 /disk2 ext3 defaults 2 2

save and exit

3. sudo mount -a
He got error at line 11 (the new added line).

Then I advised him to change the 2 2 to 0 0  
But he got this error again.

Where is the problem ?
How to mount his hard disk /dev/sdb1 to /disk2 ?
What is wrong ?

Thanks ahead.
He is my first GNU/Linux Ubuntu convert so I really need to help him + he got my cellphone number so I can't escape ;)

---

### Post by taurus on 2008-01-28
Is /dev/sdb1 an external USB harddrive?

Post both

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by MaximB on 2008-01-28
Ho damn , he got a Russian version of Ubuntu above all.

He got a SATA drive not USB.
anyway : 

```
&#1044;&#1080;&#1089;&#1082; /dev/sda: 80.0 &#1043;&#1041;, 80060424192 &#1073;&#1072;&#1081;&#1090;
255 heads, 63 sectors/track, 9733 cylinders
Units = &#1094;&#1080;&#1083;&#1080;&#1085;&#1076;&#1088;&#1099; of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28672866

&#1059;&#1089;&#1090;&#1088;-&#1074;&#1086; &#1047;&#1072;&#1075;&#1088;     &#1053;&#1072;&#1095;&#1072;&#1083;&#1086;       &#1050;&#1086;&#1085;&#1077;&#1094;       &#1041;&#1083;&#1086;&#1082;&#1080;   Id  &#1057;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;
/dev/sda1   *           1        9356    75152038+  83  Linux
/dev/sda2            9357        9733     3028252+   5  &#1056;&#1072;&#1089;&#1096;&#1080;&#1088;&#1077;&#1085;&#1085;&#1099;&#1081;
/dev/sda5            9357        9733     3028221   82  Linux &#1089;&#1074;&#1086;&#1087; / Solaris

&#1044;&#1080;&#1089;&#1082; /dev/sdb: 164.6 &#1043;&#1041;, 164696555520 &#1073;&#1072;&#1081;&#1090;
255 heads, 63 sectors/track, 20023 cylinders
Units = &#1094;&#1080;&#1083;&#1080;&#1085;&#1076;&#1088;&#1099; of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90df978a

&#1059;&#1089;&#1090;&#1088;-&#1074;&#1086; &#1047;&#1072;&#1075;&#1088;     &#1053;&#1072;&#1095;&#1072;&#1083;&#1086;       &#1050;&#1086;&#1085;&#1077;&#1094;       &#1041;&#1083;&#1086;&#1082;&#1080;   Id  &#1057;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;
**/dev/sdb1               1       20023   160834716    b  W95 FAT32**
```

o, now I'm starting to get it ...
How come he has FAT32 when in the "mount" he has it as ext3 ???

---

### Post by taurus on 2008-01-28
Well, you have to ask him how he can manage to mount vfat as an ext3 then.  Meanwhile you need to edit /etc/fstab and modify the entry for /dev/sdb1 to

```
/dev/sdb1   /disk2   vfat   defaults,umask=000   0   0
```
Then, reboot and see if it shows up on the list below.

```
df -h
```

---

### Post by MaximB on 2008-01-28
Thanks I'll try to explain it to him.
But I still don't get how he managed to mount it with ext3 and it worked ?

---

