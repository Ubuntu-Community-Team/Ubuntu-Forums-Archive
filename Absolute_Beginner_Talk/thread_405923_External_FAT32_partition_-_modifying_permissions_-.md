---
title: "External FAT32 partition - modifying permissions - fstab and mtab"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by nicketynick on 2007-04-10
Hi,
I have an external FAT32 partition that is automounting (using Dapper), without r/w permissions for all users. It doesn't have an entry in the fstab file at all, the entry seems to be in the mtab file. What is the best way give all users full permissions to this partition? I've seen this how-to [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) in a couple of places, but am confused by the fstab vs mtab situation, so I'm not confident I won't be screwing things up!
Many thanks!

---

### Post by taurus on 2007-04-10
The best way is to add an entry in /etc/fstab with umask set to 000, **umask=000**.  If you are not sure how to do that, post the output of this command from a terminal and maybe I can walk you through the whole process.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That is a lower case letter l, not number 1.

---

### Post by nicketynick on 2007-04-10
Hi taurus,
Thanks for the offer! Unfortunately, I'm not at my machine, but here's the basics:
fstab has mounts for 2 internal partitions - hda1 & hda5, I believe.
The external drive is automounting 2 partitions as sda1 & sda5. Here is what I found in the file etc/mtab:
dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-28-386/volatile tmpfs rw 0 0
/dev/sda1 /media/NTFS\040Drive ntfs rw,nosuid,nodev,uid=1000,gid=1000,umask=077,iochar set=utf8 0 0
/dev/sda5 /media/DRV4_VOL2 vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid =1000,umask=077,iocharset=utf8 0 0

Currently there aren't any lines in fstab related to sda1 or sda5, which is why I'm a little confused - if I add mounting configuration for these partitions in fstab, as directed in the how-to I've linked to, will it screw things up?

---

### Post by taurus on 2007-04-10
Can you post the output of these two commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by nicketynick on 2007-04-10
Will do, but it won't be for about 4 hours (if the wife doesn't co-opt my time before then!) I was hoping to have marching orders before I got there....

---

### Post by nicketynick on 2007-04-10
I've found the following thread:
[http://ubuntuforums.org/showthread.php?t=295143&page=2&highlight=automounting+external](http://ubuntuforums.org/showthread.php?t=295143&page=2&highlight=automounting+external)
which seems to conclude that I will have to add mounts for the external drive in the fstab, which should override the PnP functionality that is automounting them. Am I interpreting this correctly?

---

### Post by nicketynick on 2007-04-10
Here is the output, as requested: (sorry its late - as usual, my time is not my own!)
test@test-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 30.0 GB, 30003240960 bytes
255 heads, 63 sectors/track, 3647 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3495    28073556   83  Linux
/dev/hda2            3496        3647     1220940    5  Extended
/dev/hda5            3496        3647     1220908+  82  Linux swap / Solaris

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12338    99104953+   7  HPFS/NTFS
/dev/sda2           12339       24792   100036755    f  W95 Ext'd (LBA)
/dev/sda5           12339       24792   100036723+   b  W95 FAT32
test@test-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Hope this is helpful. What do you advise?

Thanks very much!

Nick

---

### Post by nicketynick on 2007-04-11
Polite bump - there sure is a lot of activity here!

---

### Post by taurus on 2007-04-11
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```

/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222   0   0
/dev/sda5   /media/sda5   vfat   iocharset=utf8,umask=000   0   0

```
Save the changes.  Then, create two new mount points and either mount them or reboot your machine.

```
sudo mkdir /media/sda1 /media/sda5
sudo mount -a
df -h
```

---

### Post by nicketynick on 2007-04-12
Thanks taurus, I appreciate your time - I'll see if I can get this done tonight - with luck I'll only be back to say thanks again!

---

