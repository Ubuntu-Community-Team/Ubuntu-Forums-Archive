---
title: "second hard drive not writable"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by newway on 2007-06-01
I installed Ubuntu 7.04 on my desktop with 2x250 SATA harddrives (/dev/sda and /dev/sdb).
At the beginning we would like to use RAID1 but didn't manage to install Ubuntu with that so
we have to disable the raid and install the OS in sda.
sda contains only 2 partitions, sda1 ext3 and sda2 swap.
now I would like to mount the second hard disk sdb (formatted as single ext3) to the system by

sudo mkdir /media/sdb
sudo chmod 755 /media/sdb
sudo mount -t ext3 /dev/sdb1 /media/sdb


everything seems to work, and I copied a bunch of files to try it out.
However, after I added auto mount to /etc/fstab  and restart, 
sdb is mounted as readonly , worst still, all the files are gone... 

I can manually umount and mount again, but it is still read only....
If I format the whole drive again, I can mount it as read-write, and I am toally confused...
here is my /etc/fstab file details:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8425bc91-2584-4ddb-b9d4-932dab271c1a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=74ef64f6-5993-4b89-ae01-f07a1d6748c7 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1       /media/sdb      ext3    rw,errors=remount-ro    0       0

(note that if I change the type from "w,errors=remount-ro" to "defaults" it is still the same.

hope someone can help me out here. thanks.

---

### Post by ugm6hr on 2007-06-01
Have to say, I don't understand linux that well either, but this got my additional ext3 partition automounting and working:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

