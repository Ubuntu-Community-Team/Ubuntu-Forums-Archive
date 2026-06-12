---
title: "Problem mounting an extra internal hard drive"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by jkreef on 2008-01-25
I know from my days of windows that I have an extra internal hard drive. However I am unable to mount it. Here is what I did to try to mount it:
> 
sudo fdisk -l

and with that I came up with:
> 
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris


So I searched the forum on how to mount hard drives and came up with sudo pmount dev/HDNAME.
     I tried this, found that I didn't have pmount, installed pmount tried again and it said the the hard drive was not removable. So I searched the forum for mounting internal hard drives and came up with:
> 
sudo mount /dev/sda2 /MOUNTLOCATION

But I couldn't figure out what to put at MOUNTLOCATION. I searched again and came up with:
> 
 sudo mount /dev/sda2 /home -o user,rw

But it came up with the error:
[Quote]
mount: you must specify the filesystem type
[Quote]
So if anyone knows what to do I would be very grateful. Thanks in advance.

---

### Post by overdrank on 2008-01-25
> **jkreef said:**
> I know from my days of windows that I have an extra internal hard drive. However I am unable to mount it. Here is what I did to try to mount it:

and with that I came up with:

So I searched the forum on how to mount hard drives and came up with sudo pmount dev/HDNAME.
     I tried this, found that I didn't have pmount, installed pmount tried again and it said the the hard drive was not removable. So I searched the forum for mounting internal hard drives and came up with:

But I couldn't figure out what to put at MOUNTLOCATION. I searched again and came up with:

But it came up with the error:
[Quote]
mount: you must specify the filesystem type
[Quote]
So if anyone knows what to do I would be very grateful. Thanks in advance.

HI and are you sure that you have a second physical hard drive because it is not shown in 
```
Device Boot Start End Blocks Id System
/dev/sda1 * 1 13995 112414806 83 Linux
/dev/sda2 13996 14593 4803435 5 Extended
/dev/sda5 13996 14593 4803403+ 82 Linux swap / Solaris
```
Are you sure that it was not a partition.

---

### Post by bwtranch on 2008-01-25
You also have to tell it to put a filesystem on it. The best tutorial for this, that I know of, is the Gentoo web site.

---

### Post by jkreef on 2008-01-25
Gentoo. Thanks so much!

---

### Post by dcstar on 2008-01-25
Install the **pysdm** package and then System-Administration-Storage Device Manager, that is what these tools are for.

---

### Post by jkreef on 2008-01-25
For some reason only my hard drive that I have Linux installed on comes up. I believe that I need sda2 however it does no show up on the storage device menu that you showed me. Is there something I could do to fix this?

---

