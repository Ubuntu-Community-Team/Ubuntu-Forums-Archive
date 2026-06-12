---
title: "Mount ext3 partition"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by nyonga on 2007-02-25
Help needed please. I recently edited /etc/fstab file while trying to allow read/write permissions which gave alot of problems on booting up. The problems was solved, however, I would like to allow permission to my partitions but am very cautious. my sudo fdisk -l loks like this:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         608     4883728+  12  Compaq diagnostics
/dev/hda2   *         609        3995    27206077+   7  HPFS/NTFS
/dev/hda3            5408        7296    15173392+   f  W95 Ext'd (LBA)
/dev/hda4            3996        5407    11341890   83  Linux
/dev/hda5            5408        5472      522049+  82  Linux swap / Solaris
/dev/hda6            5473        7296    14651248+  83  Linux
/dev/hda7            5473        5473           0+  83  Linux

Currently hda1, 2 and 6 mounts automatically, however, hda3 does not. I would like to mount hda2, 3 and 6 and have read/write permission on them. Checking /etc/fstab file I notice hda3 is missing:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4 -- converted during upgrade to edgy
/dev/hda4   /   ext3   defaults,errors=remount-ro   0   1
# /dev/hda1 -- converted during upgrade to edgy
UUID=40C8440BC843FE22 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=4C54A5A254A58EF0 /media/hda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda6 -- converted during upgrade to edgy
/dev/hda6   /media/hda6   ext3   defaults   0   1
# /dev/hda5 -- converted during upgrade to edgy
UUID=fd4e7c29-2c39-46a2-b6f0-1ee3d4b36606 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

how can I do this

---

### Post by taurus on 2007-02-25
Didn't I just show you how to change ownership of /media/hda6 so you can write to it?

And again, /dev/hda3 is your extended partition and you cannot mount an extended partition.

You cannot not write to ntfs filesystem with ntfs driver.  If you want to write to it, you need to install ntfs-3g.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Kateikyoushi on 2007-02-25
Hda3 is an extended partition you can not mount it.

---

### Post by nyonga on 2007-02-25
I am sorry Taurus, still am experiencing problem with permission for /media/hda6, although it mounts. sorry for that for not highlighting that.

---

### Post by taurus on 2007-02-25
Are you able to write to /media/hda6 with your account?  What's the output of this command from a terminal?

```
ls -la /media
```

---

### Post by nyonga on 2007-02-25
am not able to write on hda6 with my account, I guess it si still root. the command ls -la /media output is:

total 48
drwxr-xr-x  7 root  root   4096 2007-02-25 15:20 .
drwxr-xr-x 21 root  root   4096 2007-02-14 09:54 ..
lrwxrwxrwx  1 root  root      6 2007-01-25 23:28 cdrom -> cdrom0
drwxr-xr-x  2 root  root   4096 2007-01-25 23:28 cdrom0
drwxrwxrwx  1 root  root   8192 2007-02-25 11:05 hda1
drwxrwxrwx  1 root  root   8192 2007-02-25 15:47 hda2
drwxr-xr-x  3 root  root   4096 2007-01-25 23:28 hda6
drwx------ 15 henry henry 16384 1970-01-01 09:00 usbdisk

---

### Post by taurus on 2007-02-25
I assume your username is **henry**, right!

```
sudo chown -R **henry**:**henry** /media/hda6
ls -la /media
```

---

### Post by nyonga on 2007-02-25
> **taurus said:**
> I assume your username is **henry**, right!

```
sudo chown -R **henry**:**henry** /media/hda6
ls -la /media
```

Hi Taurus,
You are Godsend, Thanks a lot I can now write on hda6. Sorry for my sloppiness in linux, am still trying to get use to linux platform, and I guess am loving it even more. Cheers. 
As for /dev/hda3 can I reformat it so that I can be able to mount/write on it. Any ideas

---

### Post by taurus on 2007-02-25
If something didn't work, just say it and we would work on it.

On the other hand, you cannot mount or reformat /dev/hda3 since it's an extended partition.  In fact, if you reformat /dev/hda3, you will probably screw up all the logical partitions under it: /dev/hda4, /dev/hda5, /dev/hda6, & /dev/hda7.  Therefore, don't worry about /dev/hda3 because there is no space left unused.  Everything is taking up by /dev/hda4, /dev/hda5, & /dev/hda6 (although /dev/hda7 is an empty partition).

Here's something for you to read.

[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

---

### Post by nyonga on 2007-02-25
Thanks alot for the thread, I guess I have leave to everything the way it is. Cheers for great help keep it up!

---

### Post by Patrick K on 2007-02-25
An extended partition is a container to hold other partitions. You cannot read or write to it. As Taurus says, if you mess with it you will lose all the data in the partitions inside it.

---

