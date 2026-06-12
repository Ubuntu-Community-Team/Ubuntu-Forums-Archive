---
title: "2 qustions!"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Stuki on 2007-06-14
#1=
I have to identical partitions with Ubuntu on it which one can I format/delete?
[[IMG]http://img373.imageshack.us/img373/4205/screenshotfilebrowsernf4.th.png[/IMG]](http://img373.imageshack.us/my.php?image=screenshotfilebrowsernf4.png)[[IMG]http://img472.imageshack.us/img472/7105/screenshotfilebrowser1hk3.th.png[/IMG]](http://img472.imageshack.us/my.php?image=screenshotfilebrowser1hk3.png)

#2
I can't do anything in any folder... Etc I'm trying to extract a skin into /usr/share/amsn/skins and it says: 
[[IMG]http://img372.imageshack.us/img372/6681/screenshotfilerollerrr4.th.png[/IMG]](http://img372.imageshack.us/my.php?image=screenshotfilerollerrr4.png)

---

### Post by Inxsible on 2007-06-14
> **Stuki said:**
> #1 I have to identical partitions with Ubuntu on it which one can I format/delete?

#2 I can't do anything in any folder... Etc I'm trying to extract a skin into /usr/share/amsn/skins and it says: 


For your first problem post your fstab and fdisk -l

```
sudo fdisk -l
gksudo gedit /etc/fstab
``` -l is lowercase L

For the second one, which folder are you trying to extract to ? Its probably a permissions issue.

---

### Post by Stuki on 2007-06-15
Disk /dev/sda: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           2       16033+  12  Compaq diagnostics
/dev/sda2   *           3        1348    10811745    c  W95 FAT32 (LBA)
/dev/sda3            1349        2213     6948112+   f  W95 Ext'd (LBA)
/dev/sda4            2214        2480     2144677+  83  Linux
/dev/sda5            1349        2192     6779398+  83  Linux
/dev/sda6            2193        2213      168651   82  Linux swap / Solaris
stuki@Ubuntu1:~$ 

and

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=5dd83e6b-6029-486c-ada7-c3905dddc959 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=0C7E-12DA  /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda4
UUID=401960d8-4475-427a-af13-ecfb83625afb /media/hda4     ext3    defaults        0       2
# /dev/hda6
UUID=10daecfc-2e44-1fa5-f0f9-8507b56b6dc7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Stuki on 2007-06-15
bump!

---

### Post by diatribe on 2007-06-15
it looks like you can remove the hda4 partition, also for copying to /usr/* you would have to run nautilus as root, in a terminal type:

sudo nautilus

and then it will let you copy them

---

### Post by Stuki on 2007-06-18
how can I delete it...

(BTW the "sudo nautilus" worked thx...)

---

### Post by Stuki on 2007-06-20
bump:popcorn:

---

### Post by gdoermann on 2007-06-20
[GParted LiveCD]("http://gparted.sourceforge.net/livecd.php").  Just burn the CD then pop it in and reboot your computer.  It has a graphical user interface to help you along the process, and won't have problems with permissions and active partitions.  Also, it comes pre-installed for configuring almost all the different types of partitions.

---

### Post by gdoermann on 2007-06-20
Oh, then just delete the partition and create a new one, or expand the other one.

---

### Post by Inxsible on 2007-06-20
Just a thought.
 
Maybe hda4 is not a different partition..just another mountpoint for the root. If you are sure they are different partition, then you can go ahead and delete hda4 and merge it with any other or create a new partition altogether like the previous poster said

---

