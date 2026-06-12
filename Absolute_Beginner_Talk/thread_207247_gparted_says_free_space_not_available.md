---
title: "gparted says free space not available"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by Sebastian1986 on 2006-07-01
Hey..
I installed UBuntu using the following layout:
/dev/hda1 Linux ext3 mount point : "/"
/dev/hda2 EXTENDED PARTITION
               /dev/hda5 ext3 mount point: "/usr"
               /dev/hda6 and /dev/hda7 swap partitions....


After installation I added some more partitions using the GNOME partition editor (gparted):
/dev/hda8 vfat 
/dev/hda10 XFS 
/dev/hda9 ReiserFS 

I want to have the following mount point:
/dev/hda8 should be mounted in /home/windows
/dev/hda10 should be mounted in /opt
/dev/hda9 should be mounted in /home/me


I edited the /etc/fstab to make it look like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /usr            ext3    defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda8       /home/windows   vfat    defaults        0       0
/dev/hda10      /opt            XFS     users,umask=000 0       0
/dev/hda9       /home/me      ReiserFS        users,umask=000 0       0

And I restarted my computer..

However, when I now go Administration-->Disk Manager, those partition are shown as inaccessible and it says that "free space not available".

ANy ideas ??

p.s i also tried running mkfs for each newly created partition but no results.

---

