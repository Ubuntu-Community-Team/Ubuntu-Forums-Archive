---
title: "mounting a ubuntu harddrive on a kubuntu harddrive"
date: 2006-08-03
forum: Absolute Beginner Talk
---

### Post by BrandonSmith15 on 2006-08-03
im trying to mount the ubuntu hard drive which is 80 GB hard drive on kubuntu harddrive which is 40 GB. plese help

here is some info if it helps

brandon1@brandon1-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


and more info

brandon1@brandon1-desktop:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9491    76236426   83  Linux
/dev/hda2            9492        9726     1887637+   5  Extended
/dev/hda5            9492        9726     1887606   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4664    37463548+  83  Linux
/dev/hdb2            4665        4865     1614532+   5  Extended
/dev/hdb5            4665        4865     1614501   82  Linux swap / Solaris

---

### Post by catlett on 2006-08-03
To mount it all the time, you have to add it to the /etc/fstab file. First you need to make a directory for it. Open the terminal
```
sudo mkdir /media/ubuntu
```
```
sudo kate /etc/fstab
```
Then add this line to the file. Save and reboot. It will be mounted in the folder ubuntu which will be in the media folder. If you have "icons viewable" enabled, it will be an icon on your desktop as well
```
/dev/hda1       /media/ubuntu           ext3    defaults        0       2
```
So your file should look like this 
```
proc                /proc                 proc      defaults              0    0
/dev/hdb1        /                       ext3      defaults,errors=remount-ro   0 1  
/dev/hdb5        swap                 sw                                  0    0
/dev/hdc         /media/cdrom0   udf,iso9660 user,noauto    0    0
/dev/hda1       /media/ubuntu    ext3      defaults               0     2
```

---

### Post by BrandonSmith15 on 2006-08-03
im geting this when i try to mount it now  only root can mount /dev/hda1 on /media/ubuntu

---

### Post by catlett on 2006-08-03
You're going to have to give it the right permissions. In the terminal enter 
```
sudo chown -R brandon1:brandon1 /media/ubuntu
sudo chmod -R 755 /media/ubuntu
```
Do this to remount the partitions without restarting 
```
sudo mount -a
```

---

