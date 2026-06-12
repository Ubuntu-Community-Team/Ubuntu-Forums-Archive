---
title: "2nd Hard-drive Help"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by deaster2 on 2007-09-01
I am at my wits end...
I have searched the forums and tried everything I could find to
no avail.
I changed my WinXP box to Fiesty and installed a second hard-drive.
For  the life of me, I can't write to it or even look in the lost+found
folder on it. 
Here is my output from fstab and fdisk -l

deaster@deaster-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14854   119314723+  83  Linux
/dev/sda2           14855       14946      738990    5  Extended
/dev/sda5           14855       14946      738958+  82  Linux swap / Solaris

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3649    29310561   83  Linux
deaster@deaster-desktop:~$ sudo mkdir /media/ddrive
mkdir: cannot create directory `/media/ddrive': File exists

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e3bb2520-fdc1-419e-9be0-e419ec96feca /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b0b39b60-4655-419d-a11b-d3e038f51851 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
**/dev/sdb1	/media/ddrive	ext3	defaults	0 0**

Any ideas what I'm doing wrong...

---

### Post by taurus on 2007-09-01
If you want to write to it, you need to change the ownership of /media/ddrive from root to your login name.  _Assuming_ your login name is **deaster**, do

```
sudo chown -R **deaster**:**deaster** /media/ddrive
ls -la /media
```

---

