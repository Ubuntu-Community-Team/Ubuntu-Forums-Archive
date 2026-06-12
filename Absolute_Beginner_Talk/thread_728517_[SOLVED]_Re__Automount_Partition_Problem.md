---
title: "[SOLVED] Re:  Automount Partition Problem"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by tstack77 on 2008-03-18
I'm having a problem following [THIS]("http://www.psychocats.net/ubuntu/mountwindows") tutorial. When I get to:

[I]Next, let's edit the fstab file:

sudo nano /etc/fstab

This is what it might look like before we change it:

proc /proc proc defaults 0 0
/dev/hda6 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 /home ext3 defaults 0 2
**[SIZE="3"]/dev/hda1 /media/hda1 ntfs defaults 0 0[/SIZE]**
/dev/hda7 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0[/I]

My windows partition isn't recognized at all. All that fstab displays is my ext3 and swap partitions.

Where am I going wrong?

---

### Post by Moop on 2008-03-18
Is your windows partition on the same hard drive as Ubuntu? Did the command ```
sudo fdisk -l
``` show your windows partition? Did you unmount the partition before you ran the commands?

---

### Post by tstack77 on 2008-03-18
Yes it's on the same partition (I only have the one disk). I followed the intstructions on the tutorial and unmounted /media/disk at the start.

fdisk -l:

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00057bc7

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       19467   156368646    7  HPFS/NTFS
/dev/hdc2           19468       24116    37343092+  83  Linux
/dev/hdc3           24117       24321     1646662+   5  Extended
/dev/hdc5           24117       24321     1646631   82  Linux swap / Solaris

/etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc2
UUID=4b355410-324d-4ecb-a3f0-16b8ffb4c8af /               ext3    defaults,erro$
# /dev/hdc5
UUID=b2c5efdf-c157-42c7-8277-18d072c321c3 none            swap    sw           $
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by Moop on 2008-03-18
You should be able to just add the line to your fstab. 

**/dev/hdc1       /windows        ntfs    nls=utf8,umask=0222        0       0**

then save it and finish the tutorial steps.

---

### Post by tstack77 on 2008-03-19
Excellent!

Thank you

---

