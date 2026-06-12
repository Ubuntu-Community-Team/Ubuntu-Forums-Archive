---
title: "[SOLVED] vista installed harddrive has disappeared !!!"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by halilakin on 2008-02-17
hi !


i am running windows vista and ubuntu 7.10 together on my harddisk partitions. but today something strange happened. when i restarted ubuntu , it started to check sda1 as regular for mounting more than some number. there was nothing unordinary. but since then i cannot see my sda1 partition any more when running ubuntu :(

how can i fix this problem ?
thanks in advance pals.

---

### Post by jan quark on 2008-02-17
run these commands and post the putput here
let's see what partitions are still tere

```
mount 
```

```
sudo fdisk -l
```
```

cat /etc/fstab
```

---

### Post by halilakin on 2008-02-17
mount :


/dev/sda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)



sudo fdisk -l :

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe56c7a86

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16119   129474497    7  HPFS/NTFS
/dev/sda2           18690       19457     6168960    7  HPFS/NTFS
/dev/sda3           16120       16181      498015   82  Linux swap / Solaris
/dev/sda4           16182       18689    20145510   83  Linux

Partition table entries are not in disk order


(sda1 -> vista
 sda2 -> hp recovery)


cat /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=fcb8fb75-b7ea-4079-9aab-70123590a9d5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=557E06E5671EFA8D /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=2C88743C8874071C /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=75a40304-1872-431c-9868-f5316efe2005 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0



thnks in advance and sorry for the confusion again.

---

### Post by jan quark on 2008-02-17
run 

```
ls -la /media
```

and post the output

---

### Post by halilakin on 2008-02-17
total 20
drwxr-xr-x  5 root root 4096 2008-02-17 18:35 .
drwxr-xr-x 23 root root 4096 2008-02-17 13:41 ..
lrwxrwxrwx  1 root root    6 2008-01-21 13:01 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-01-21 13:01 cdrom0
-rw-r--r--  1 root root    0 2008-02-17 18:35 .hal-mtab
-rw-------  1 root root    0 2008-02-17 15:18 .hal-mtab-lock
drwxr-xr-x  2 root root 4096 2008-01-21 13:01 sda1
drwxr-xr-x  2 root root 4096 2008-01-21 13:01 sda2

---

### Post by sisco311 on 2008-02-17
can you mount it manually?
```
sudo mount /dev/sda1 /media/sda1
```

---

### Post by jan quark on 2008-02-17
well the partition is displayed in media correctly

what happens if you navigate to the media folder

places > computer > filesystem > media

can you access all partitions? are they displayed in this folder?

---

### Post by halilakin on 2008-02-17
wow. i solved the problem with your helps. thanks jan quark and sisco311.

after trying to mount the driver manually , the terminal adviced me to shut down windows cleanly.the last time i used vista it was stuck at shutting down screen and i had to use power button to shut it down.So i changed to vista and closed it clearly this time.

And that was the problem. Because Vista hasn't been closed properly, i wasn't able to reach it from my Ubuntu.

thanks guys.

---

### Post by jan quark on 2008-02-17
yea that problem is solved so often by doing this

haven't thought about this ](*,)

---

