---
title: "Permission (read and write) etc. (on partition)"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Corbin on 2007-09-03
Hey, I have 3 partition on my hard drive. 
called (in linux)

LOCAL DISK (windows)
non_windows (music,download, etc)
filesystem (linux)

Current i ONLY have permission to read/write to "filesystem" and not to "non_windows or LOCAL DISK"... I have tried switching the permission a few different ways that i found on the forums... and none of them worked.. 

I am running Ubuntu Feisty Fawns.

Any help would be SWEET

-Thanks

---

### Post by yabbadabbadont on 2007-09-03
In a terminal window, please run, and post the output of, the following commands:
```
sudo fdisk -l
mount
cat /etc/fstab
id

```

---

### Post by Corbin on 2007-09-03
**sudo fdisk -l**
```


maximus@maximus-laptop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1186     9526513+   7  HPFS/NTFS
/dev/hda2            3218        4864    13229527+  83  Linux
/dev/hda3            1187        3217    16314007+   f  W95 Ext'd (LBA)
/dev/hda5            1187        3138    15679408+   7  HPFS/NTFS
/dev/hda6            3139        3217      634536   82  Linux swap / Solaris

Partition table entries are not in disk order


```


**mount**
```


maximus@maximus-laptop:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hda1 on /media/LOCAL DISC type ntfs (rw,nosuid,nodev,umask=222,utf8)
/dev/hda5 on /media/non_windows type ntfs (rw,nosuid,nodev,umask=222,utf8)


```

**cat /etc/fstab**
```
maximus@maximus-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=79edb168-7e7f-479f-9997-ed620243b375 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=47725171-98f9-4f86-a3f8-df36db545043 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

**id**
```


maximus@maximus-laptop:~$ id
uid=1000(maximus) gid=1000(maximus) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),119(fuse),1000(maximus)

```

---

### Post by yabbadabbadont on 2007-09-03
NTFS partitions are read only using the default drivers in the kernel.  To get read-write support for them, you need to install the ntfs3g package.  Here are the instructions on how to install and configure it: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

EDIT: Hmmm.  It looks as though they have been mounted rw in the mount output.  Have you already installed ntfs3g?

---

### Post by Harpoon on 2007-09-03
I thought ntfs3g was part of the feisty package (it was in mine).   A shortcut to solving the problem might be to sudo apt-get install ntfs-config (or search for it in the package manager), then run sudo ntfs-config in a terminal window.  When the gui pops up, just select the options you want (makes mounting ntfs on usb easy).

---

### Post by yabbadabbadont on 2007-09-03
That is all spelled out in the help article to which I linked.  :D

---

### Post by Corbin on 2007-09-03
No, i have not installed/ran ntfs3g... 
(at least nothing runs in the termanal when i do ntfs3g).... 

So i guess i will go ahead and do what you suggested and install/configure it. 

-Thanks, i will let you know how it goes.

---

### Post by Harpoon on 2007-09-03
yabbadabbadont:
So it is.  There be lag on the net.  Maybe it gets confused crossing the international date line.  Saved your (very nice) link for future reference.  Thanks

---

### Post by Corbin on 2007-09-04
I ran through the process and now i can no longer see my "LOCAL DISK" (in computer) that is. and i still cannot write to "non_windows"... 

But the install/update all worked and installed correctly..

---

### Post by yabbadabbadont on 2007-09-04
:?  Did you also follow the instructions for installing/running the ntfs-config program?

(This is why I always stick to FAT32 partitions for Windows.  ;))

---

### Post by Corbin on 2007-09-04
lol.... yes i ran the ntfs-config program...

I also went back and tried the manual configure and now i have local disk back but i cant even see my "non_windows"....

---

### Post by Corbin on 2007-09-05
Anything?

---

