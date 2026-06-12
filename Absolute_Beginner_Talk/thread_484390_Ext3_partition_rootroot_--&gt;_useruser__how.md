---
title: "Ext3 partition root:root --&gt; user:user  how??"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Thorun on 2007-06-25
It's a very old question - but i just can't seem to make it work. No matter how many guides i have read through.

The problem: I have a Ext3 partition on /dev/sda7 and i can make it show up on my desktop (as i would like wery much) but in the terminal with ls -l the privileges is root:root and not user:user which is what would like to. 

sudo fdisk -l
```

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        1431    11414182+   7  HPFS/NTFS
/dev/sda3            1432        7296    47110612+   f  W95 Ext'd (LBA)
/dev/sda5            1432        1680     2000061   82  Linux swap / Solaris
/dev/sda6            1681        3504    14651248+  83  Linux
/dev/sda7            3505        5328    14651248+  83  Linux
/dev/sda8            5329        7296    15807928+   b  W95 FAT32

```


sudo gedit /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=2009773d-7d7e-40a5-a3ca-90aca6965b86 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=07D6-0202  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
#UUID=32A01C98A01C651F /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=d9e43de2-ffc4-48ed-8b64-e89626726b65 /media/linux-data     ext3    defaults        0       2
# /dev/sda8
#UUID=B6D1-8BAF  /media/sda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=9bf95716-5b66-49ea-a368-8c562a4ae8c8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```



what should i do, to make my sda7 partition rwx for the user (me)? and not only for the root?

---

### Post by fdrake on 2007-06-25
sudo chown username /dev/sda7
sudo chmod 755 /dev/sda7

---

### Post by yabbadabbadont on 2007-06-25
In a terminal window, run:
```
sudo chown user:user /media/linux-data
```
Substitute your username for "user" in my example.  Then you should be able to create files/directories in /media/linux-data as your user.

Edit: Too slow.  :)

---

### Post by Thorun on 2007-06-25
@fdrake

have just typed your suggestion in a Terminal Window. 
Nothing have changed... Still no access.

---

### Post by yabbadabbadont on 2007-06-25
> **Thorun said:**
> @fdrake

have just typed your suggestion in a Terminal Window. 
Nothing have changed... Still no access.

That is because he gave you the wrong commands.  You don't change the device, but the directory on which the device is mounted.  Try my example and see if it works.

---

### Post by Thorun on 2007-06-25
I don't know what have happened. I tried to delete all my folders i desperately have made to mount the /dev/sda7 to. 

Now, my fstab-file is back to the way it was originally (when i couldn't write to sda7), but somehow i now *can*. 

```
rune@dell-uff:/media$ ls -l
total 28
dr-xr-xr-x 1 root root 8192 2007-06-25 01:36 160samsung
lrwxrwxrwx 1 root root    6 2007-06-25 22:46 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2007-06-25 22:46 cdrom0
drwxr-xr-x 2 root root 4096 2007-06-25 22:46 sda1
drwxr-xr-x 2 root root 4096 2007-06-25 22:46 sda2
drwxr-xr-x 4 rune rune 4096 2007-06-26 01:24 sda7
drwxr-xr-x 2 root root 4096 2007-06-25 22:46 sda8

```
as you can see, did the sda7 folder get rune:rune instead of root:root like all of the others. But i really don't know what did the trick. 


sudo gedit /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=2009773d-7d7e-40a5-a3ca-90aca6965b86 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=07D6-0202  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
#UUID=32A01C98A01C651F /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=d9e43de2-ffc4-48ed-8b64-e89626726b65 /media/sda7     ext3    defaults        0       2
# /dev/sda8
#UUID=B6D1-8BAF  /media/sda8     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=9bf95716-5b66-49ea-a368-8c562a4ae8c8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```


and now i'm able to write to the disk. 
I don't know if it was yabbadabbadont's code that did the trick. But somehow what didn't work before now work - with the exact same files and folders.

---

