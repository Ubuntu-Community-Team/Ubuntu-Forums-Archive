---
title: "hard drive disapeared"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by DrPppr242 on 2007-05-16
my second hard drive was working yesturday and was on my desktop as disk but it's gone today, can someone help me get it back?

---

### Post by bodhi.zazen on 2007-05-16
You mean the desktop icon is gone or you can not access the drive at all ?

Did you re-boot ?

Can you provide more information, mount point, fstab line, outppur of ```
mount
sudo fdisk -l
```

---

### Post by DrPppr242 on 2007-05-16
I can't access it at all I it was in /media/disk but now it's gone.

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4310    34620043+  83  Linux
/dev/sda2            4311        4500     1526175    5  Extended
/dev/sda5            4311        4500     1526143+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               3       14593   117202207+  83  Linux


(btw it's sdb1)

---

### Post by taurus on 2007-05-16
Try

```
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
df -h
```

---

### Post by DrPppr242 on 2007-05-16
that worked thanks, now will it automaticaly mount next time I boot?

---

### Post by bodhi.zazen on 2007-05-17
> **DrPppr242 said:**
> that worked thanks, now will it automaticaly mount next time I boot?

If you want the disk/partition to automatically mount at the time of boot you need a line in fstab.

```
gksudo gedit /etc/fstab
```

Enter or modify the line for to look something like this:

> /dev/sdb1  /media/sdb1  ext3  auto,users  0  0

For more info on the subject see this link : [How to fstab](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by firedancer on 2007-05-17
mines too , tried following steps 


/dev/sdb1 /media/sdb1 ext3 auto,users 0 0

sends message back : 'command not found'

 ?

---

### Post by taurus on 2007-05-17
You need to add that line, /dev/sdb1 /media/sdb1 ext3 auto,users 0 0, to the end of your /etc/fstab if you want to mount it.  Not supposed to run it from a terminal.

```
gksudo gedit /etc/fstab
```

---

### Post by bodhi.zazen on 2007-05-17
LOL

Don't forget to make the mount point. This one you do enter into a terminal :

```
sudo mkdir /media/sdb1
```

---

