---
title: "External NTFS HELP!"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by jrsteffes on 2006-11-10
I have a external drive that I used with XP that has alot of files on it.  It is formated in NTFS and when I plug it in nothing happens, except the activity light on the drive stays on constantly.  I real need the stuff on the drive! Please Help!

---

### Post by jrsteffes on 2006-11-10
Ubuntu dosent seem to even know its there, but it worked fine with XP!

---

### Post by bodhi.zazen on 2006-11-10
LOL :lol:

With the usb drive plugged in, open a terminal and type:```
sudo fsdisk -l
```_Note_: That is a small "L" not the number 1.

Your usb device is likely listed as /dev/sda1.

If this is the case you can mount with:```
pmount /dev/sda1 usb
```
OR
```
sudo mkdir /media/usb
sudo mount /dev/sda1 /media/usb -t ntfs
```

You can then add a line in fstab:```
sudo gedit /etc/fstab
```

Add a line:> /dev/sda1 /media/usb ntfs noauto,users 0 0

If you need read-write: [ntfs-3g](http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support)

---

### Post by jrsteffes on 2006-11-10
jason@jason-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18666   149934613+  83  Linux
/dev/sda2           18667       19457     6353707+   5  Extended
/dev/sda5           18667       19457     6353676   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401   83  Linux
jason@jason-desktop:~$ 

It dosent appear to even show up, the 200Gb is a 2nd internal that is working!  Any advice?  fsdisk dosent do anything on my system so i used fdisk, are they the same?  Please help!

---

### Post by bodhi.zazen on 2006-11-10
sorry for the typo. Yes I meant fdisk....

What brand of usb drive ?

---

### Post by jrsteffes on 2006-11-10
It is a generic Mobile Disk case with a WD1200 120GB drive.

---

### Post by jrsteffes on 2006-11-10
The drive activity light stays on constantly when pluged in.

---

### Post by jrsteffes on 2006-11-10
Should I try to install the drive internally?  I have two SATA HD's and I would have to disconect one of my cd/DVD drives cause my mobo only has one IDE controler.  But if I could get the data off that would make me happy and then I could maybe fine a external case that would work with Linux.

---

### Post by bodhi.zazen on 2006-11-10
I do not know if your WD drive will work with Ubuntu.

---

### Post by jrsteffes on 2006-11-10
You think the drive itself wont work?  Or should I install it internally.  Is there drives that dont work with ubuntu?

---

### Post by jrsteffes on 2006-11-10
Anyone else have ideas???

---

### Post by bodhi.zazen on 2006-11-10
> **jrsteffes said:**
> You think the drive itself wont work?  Or should I install it internally.  Is there drives that dont work with ubuntu?

I think the drive itself will not work :(

But....

Go ahead and install it internally, but also transfer one of the (currently) internal disks to the external drive bay. Thus you can test both the drive and the external drive bay.

---

### Post by jrsteffes on 2006-11-10
The internal disks are SATA and the external drive case is for IDE so that wont work. But I will try the drive internally.

---

### Post by jrsteffes on 2006-11-10
The drive works internally, I got it mounted!!!!  Thanks for the help.

---

### Post by bodhi.zazen on 2006-11-10
:) Not much i was....

---

