---
title: "annoying drive password"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by prob69 on 2007-11-12
I previously installed Ubunto 7.10 on a partitioned drive and all worked well. I have now re-installed on a completely seperate drive. Within my computer I also have an NTFS data drive that I use in vista as well, but when I first try to access the drive in Ubuntu it asks for a password. This never used to happen before I re-installed Ubuntu
I am assuming there must be a setting somewhere to disable the password which for some reason has now changed.
How do I stop it asking for my password when I want to access this 2nd drive?.

---

### Post by noodleowns on 2007-11-12
mount it as admin maybe

---

### Post by prob69 on 2007-11-12
Very new to this, How do I do that?  I just want to click the icon and open the contents without entering password, as I did before re-install.

---

### Post by taurus on 2007-11-12
Can you post

Applications -> Accessories -> Terminal
```
sudo fdisk -l  <-- lower case letter l, not number 1
cat /etc/fstab
mount
```

---

### Post by prob69 on 2007-11-12
Here is the info as requested



Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2327    18691596   83  Linux
/dev/hda2            2328        2434      859477+   5  Extended
/dev/hda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/hdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06a0f91c

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       24792   199141707    7  HPFS/NTFS
paul@UMaster:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9f65300d-f74d-47aa-87c2-ddddd49f3678 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=93a3afbc-d1bd-4417-b672-d829d26a0516 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
paul@UMaster:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/hdd1 on /media/Data type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

---

### Post by taurus on 2007-11-12
Okay, make sure you have ntfs-3g installed on your machine first.

```
sudo apt-get update
sudo apt-get install ntfs-3g
```
Now, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdd1   /media/hdd1   ntfs-3g   defaults,locale=en_US.utf8   0   0
```
Save it.  Then create a new mount point and reboot.  Your windows, /dev/hdd1 will be mounted to /media/hdd1 each time you boot into Ubuntu.  One caution though.  Always shutdown your windows cleanly after you use it or Ubuntu would have problems mounting it.

```
sudo mkdir /media/hdd1
```
Don't worry if a message says that /media/hdd1 already exit.

---

### Post by prob69 on 2007-11-12
Just realized that I had already entered the password and could access the drive before getting all this info. Should I restart and re-post before without entering the password to access?

---

### Post by prob69 on 2007-11-12
Thats done the trick thanks!  Not sure why it worked last time without me doing anything like that but all okay now.
How you guys know what to is beyond me. Keep up the good work. We would be lost without you. Thanks again.

---

