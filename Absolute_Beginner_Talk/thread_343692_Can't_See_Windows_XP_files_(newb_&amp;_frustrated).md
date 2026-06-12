---
title: "Can't See Windows XP files (newb &amp; frustrated)"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by samson-pdx on 2007-01-21
I've spend the last 2 hours trying to figure out how to find out how to see my windows files and I'm at a total loss. If the info exists I either can't find it or don't understand it. Installing Ubuntu 6.10 is my first experience with Linux. I'm completely baffled by the terminal and have never used anything like that before and is likely the biggest part of my problem. Can anyone help me find my Windows files and explain it to me like I'm your grandmother?

I figured out how to get some of the data you may need from other posts. Here's the readout from my computer:

sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223        9542    34700400   83  Linux
/dev/sda3            9543        9729     1502077+   5  Extended
/dev/sda5            9543        9729     1502046   82  Linux swap / Solaris




# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=3b771d9e-a2f6-4fe3-9318-48a0270e3662 /               ext3    defaults,erro$
# /dev/sda5
UUID=e1f3e87a-07d2-47d7-8ace-fb89a04b811d none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0

Thank you for helping!

---

### Post by taurus on 2007-01-21
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

p.s.  It should be /dev/sda1, not /dev/hda1.

```
/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0
```

---

