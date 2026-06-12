---
title: "Restoring Partition on Flash Drive (USB Key)"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by tonycm1 on 2008-01-02
Just wanted to know if anyone can recommend some software in linux (or..err.. windows) to restore the FAT partition on my USB Flash Key.

The genious that I am (/end sarcasm) decided to leave my flash drive plugged into my PC when installing ubuntu and accidently deleted the partition table. I know the data is still on there, but I just wanted to know how I can "re-add" the partitoin so that it can read the data again.

Ideas?

---

### Post by LowSky on 2008-01-02
unless you formatted the drive, it hasn't been repartitioned, you just need to remount the flash drive
in terminal type thes two commands
```
sudo mkdir /media/usbdisk
sudo mount /dev/sdd1 /media/usbdisk
```

---

### Post by jken146 on 2008-01-02
You can find out if the partition table is still there. ```
sudo fdisk -l
```

---

### Post by LowSky on 2008-01-02
ah I knew I forgot something

```
sudo fdisk -l
```

BTW: (-l ) thats a lower case L

---

### Post by L Campbell on 2008-01-02
> **tonycm1 said:**
> Just wanted to know if anyone can recommend some software in linux (or..err.. windows) to restore the FAT partition on my USB Flash Key.

The genious that I am (/end sarcasm) decided to leave my flash drive plugged into my PC when installing ubuntu and accidently deleted the partition table. I know the data is still on there, but I just wanted to know how I can "re-add" the partitoin so that it can read the data again.

Ideas?

This might help you:-

[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

---

### Post by tonycm1 on 2008-01-02
Tried:

sudo mkdir /media/usbdisk
sudo mount /dev/sdd1 /media/usbdisk

and 

sudo fdisk -l

both didn't do anything.... for that matter, sudo fdisk -l didn't find the partition on my USB key....

As a means of last resort, I downloaded the "freebie" version of Pen Drive / Memory Stick data recovery software ([http://www.recoverdata.co.in/recover-data/downloads.html](http://www.recoverdata.co.in/recover-data/downloads.html))

That software lists all my files (which is great since I know they exist)... but I was wondering if there is a Linux alternative to this software that I can install in Ubuntu? :confused:

---

