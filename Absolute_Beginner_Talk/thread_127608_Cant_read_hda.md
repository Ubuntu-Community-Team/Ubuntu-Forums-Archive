---
title: "Cant read hda ?"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by HiSpeed15 on 2006-02-09
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    iocharset=utf8,umask=000        0
0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
 
(in Disks Manager)


Partition 2
In /dev/hda2 it says 
Filesystem:Windows virtual fat v32  
access path none
size 23.28GB(free space not available)
Status : inaccessable
I tried the "enable"button to no avail.(actually I understand why this one is not avail)
 
No list of Partition 3

Partition 4
/dev/hda4
Filesystem: extended3
access path /
size 8.91GB (6.58GB free)
Status: Accessable


/dev/hda6
Swap Partition 423.53 MiB

Partition 5
/dev/hda5
Filesystem:extended 2
access path  none
size 13.97GB (free space not available)
Status: Inaccessable

I dont understand why these two drives are "inaccessable" and havent figured out how to access or "mount" them. I looked around in the forums for something similar but more or less confused myself.

---

### Post by TrendyDark on 2006-02-09
You have to first set the access path. Next to that option in disk manager is "Browse", click that and choose a folder you'd like the drive to mount under. The best way to do this is to create a folder in your home directory for them both.

Use this guide for a better way, if you scroll lower it'll tell you how to mount them automatically at boot up.

[http://ubuntuguide.org/#mountunmountfat](http://ubuntuguide.org/#mountunmountfat)

---

### Post by taurus on 2006-02-09
Wait a second, there is something seriously wrong here...  As far as I know, you can only have 4 primary partitions but you can have as many as extended partitions as you wish.  So, /dev/hda1, /dev/hda2, /dev/hda3, /dev/hda4 are all primary partitions while /dev/hda5 and so on are extended partitions.  If you plan to have extended partition(s), then you must make the last primary partition to be logical partition so you can create extended partition(s) from there.  Since /dev/hda6 is an extended partition, it means that there shouldn't be /dev/hda4!!!  

What does the output of this command give you,

fdisk -l /dev/hda

---

### Post by HiSpeed15 on 2006-02-09
Well I maybe could have waited  awhile longer,but went ahead and deleted all those partitions and extended partitions,then reinstalled keeping the winxp on 30GB and putting Ubuntu on 50GB its reading it all now anyhow.1.8GB for a swap is pretty big but I used the auto format feature.I thought I could maybe fix that later.In the future when I ask for help I will wait for a response. Sorry bout that and Thank You.

---

