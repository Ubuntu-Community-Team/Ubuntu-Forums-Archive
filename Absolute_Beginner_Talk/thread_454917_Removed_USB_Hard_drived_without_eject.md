---
title: "Removed USB Hard drived without eject"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by jdrodrig on 2007-05-26
Hi,

I am very new to Ubuntu and I have what I think is a simple question.

I used an USB Hard drive for a while, but when I needed to leave the eject option would not work, neither the command unmount. I honestly do not remember the exact error message. I decided to just shutdown the computer and go home..... But now at home my ntfs partition that used to appear in my desktop is gone. I also do not see it in my "Places" column in Nautilus. 

My ntfs-config has both options checked and my fdisk -l gives:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5607    45038196    7  HPFS/NTFS
/dev/sda2            5608        7219    12948390   83  Linux
/dev/sda3            7220        7296      618502+   5  Extended
/dev/sda5            7220        7296      618471   82  Linux swap / Solaris

Any help would be greatly appreciated.

Daniel

---

### Post by TravMan63 on 2007-05-26
Without seeing the disk/partition, I'm not sure how these utilities will work:

In linux : fsck
Windows : chkdsk

I'd try fsck 1st, chkdsk can write back to the disk, which isn't always a good idea.

TM

> for more info, type "man fsck" in console, "help chkdsk" in a cmd window.
It appears your sda1 partition is where the NTFS partition exists

---

### Post by Ek0nomik on 2007-05-26
You probably just need to reboot or turn off your usb hard drive and turn it back on and Ubuntu will find it.

If you get that to work, reply and I will tell you how you can have it auto mount on each loading of Ubuntu or you can search the forums on how to do it, your choice.

---

### Post by jdrodrig on 2007-05-26
Thanks, the twice boot into Windows worked. I honestly thought it was a joke the "reboot twice" instructions... but I guess it must be a hidden reason.

Daniel

---

### Post by Ek0nomik on 2007-05-26
Do you want your NTFS drive to mount automatically every time you boot into Ubuntu?

---

### Post by paddyboy on 2007-05-26
He might not, but I do. ;)

---

### Post by Ek0nomik on 2007-05-26
Well, the first step is to find out where your NTFS drive is mounted.

```
fdisk -l
```

An example of what you will get:

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/**sdb1**               1       48640   390700768+   c  W95 FAT32 (LBA)

Although yours will be slightly different because it's NTFS.  (I have all my drives formatted to FAT32.)

Now you will want to create a directory for your files to sit in:

```
sudo mkdir /media/My_Files
```

(Name it whatever you wish)

Next, you want to edit your fstab file:

```
sudo gedit /etc/fstab
```

Once you have that loaded, you will want to add a line at the bottom of the file corresponding to your NTFS drive:  (NOTE:  It may not be sdb1, it might be sdbb, or sdc1, so look for what identification yours has.)

/dev/sdb1 /windows ntfs nls=utf8,umask=0222 0 0

If you want Write/Read support for your NTFS drive, you can follow this tutorial:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

Cheers!

---

