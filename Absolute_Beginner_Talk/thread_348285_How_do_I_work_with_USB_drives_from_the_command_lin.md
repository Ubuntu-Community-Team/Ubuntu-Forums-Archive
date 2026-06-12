---
title: "How do I work with USB drives from the command line?"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Phrawm48 on 2007-01-28
I have a FAT32 partition on a USB2 drive, "/dev/sda5" in the following list.

[HTML]
ric@ric-desktop:~$ fdisk -l

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6375    51207156    7  HPFS/NTFS
/dev/sda2            6376       10200    30724312+   7  HPFS/NTFS
/dev/sda3           10201       12750    20482875    7  HPFS/NTFS
/dev/sda4           12751       19929    57665317+   f  W95 Ext'd (LBA)
/dev/sda5           12751       19929    57665286    b  W95 FAT32
ric@ric-desktop:~$
[/HTML]

I can easily browse the USB drives via the Gnome GUI, but  how I can use the terminal command line (in Gnome, "Applications > Accessories > Terminal") to perform operations on this drive (cd, ls, chmod, and so on...)?

My attempts to "ls /dev/sda5/*" produce an error.

This question is evidently so newbie-ish (as in so obvious how to do it doesn't need to be explained) that I can't find an answer to it anywhere, so I thought I'd ask here...

Note that this question arises in part because I don't know how to do sudo-level commands (chmod, chown) via the GUI...

Cheers & thanks,
Ric
SFO

---

### Post by taurus on 2007-01-28
```
sudo mkdir /media/sda5
sudo mount -t vfat /dev/sda5 /media/sda5 -o iocharset=utf8,umask=000
ls -la /media/sda5
```

---

### Post by Phrawm48 on 2007-01-28
Yes!  (And I don't feel quite so foolish now that I see the commands required...)

I can now learn about the magic of scripting to automate this a bit...

Cheers and thanks much!
Ric
SFO

---

### Post by taurus on 2007-01-28
Glad to help out a fellow San Franciscan.

If you want it to mount automatically upon boot, here's a guide on how to modify your /etc/fstab.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

