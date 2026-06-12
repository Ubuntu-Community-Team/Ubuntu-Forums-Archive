---
title: "Writing Privilage to a Hard Disk"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by perito on 2008-03-16
I have sda6 in /media >> (/media/sda6)
I can read it (open it) but can write to it (unless in the terminal with sudo)
how can I write to that hard disk without the terminal?

---

### Post by perito on 2008-03-16
how can I write to that hard disk without the terminal?

---

### Post by Koybe on 2008-03-16
Whiich version of Ubuntu are you using and what type of partition is set to your external HD?

---

### Post by jken146 on 2008-03-16
Please post the output of ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```

---

### Post by perito on 2008-03-16
7.04 fiesty
and the sda6 is etc3 ... the deafult type when installing ubuntu

---

### Post by perito on 2008-03-16
```
ubuntu@ubuntu-laptop:/$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8877    71304471   83  Linux
/dev/sda2            8878       19457    84983850    5  Extended
/dev/sda5            8878        8999      979933+  82  Linux swap / Solaris
/dev/sda6            9000       14228    42001911   83  Linux
/dev/sda7           14229       19457    42001911   83  Linux
ubuntu@ubuntu-laptop:/$ 


```

```
ubuntu@ubuntu-laptop:/$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=99f765b4-2ba2-478f-a500-00b3edaf2e46 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=4a844dca-e4c4-469d-a064-ee5a5e46ee7f /media/sda6     ext3    defaults        0       2
# /dev/sda7
UUID=c0116e48-add4-403e-87a2-f763404abb7a /media/sda7     ext3    defaults        0       2
# /dev/sda5
UUID=02ff100a-2448-41e0-9bcb-e3d130981005 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
ubuntu@ubuntu-laptop:/$ 


```

---

### Post by nebu on 2008-03-16
check this if the drive is a windows ntfs partition -- [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by jan quark on 2008-03-16
try this
```

sudo chown -R username:username /dev/sda6
```

change username to your username for instance
john:john

---

