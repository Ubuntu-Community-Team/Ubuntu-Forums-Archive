---
title: "undetected WD MyBook usb ext. hard drive"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by ridgeback on 2006-11-19
I have a 160gb Western Digital external hard drive (usb) and I can't get ubuntu to recognize it for the life of me, which means very little since I am a brand new linux user.  It is connected to a usb 2.0 card with two ports, both of which work with my flash drive, so I have no idea what the problem could be.  I am using the power adapter for the drive so power isn't an issue.  On windows, the drive is detected, not as external storage, but as a MyBook, which is probably because of pre-installed WD MyBook software, which could be the issue.  Any help would greatly be appreciated as the drive contains all of my media, without which I would be forced to go back to using windows, and I do not want to do that. Thank you for your time.

Jerod

---

### Post by ReaderRat on 2006-11-19
It does sound as though you might have a software conflict. Have you tried to mount the external drive?
[**Mounting Windoze Partition**](http://www.psychocats.net/ubuntu/mountwindows)
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by ridgeback on 2006-11-19
I have tried to have a linux-savvy friend of mine mount my hard drive, but he couldn't get it.  The system just plain doesn't detect the hard drive.  fdisk -l lists my two internal hard drives and my flash drive, but not the external drive right next to the flash drive, and I don't know which usb id it is plugged into.  If you could give me a quick walk-through of how to find and mount something from a usb card that might help.  I looked at the links you gave and I just don't get what I'm supposed to do.  Every command I type in gives different output than what is assumed (perhaps because I am running ubuntu 6.10?).

---

### Post by ReaderRat on 2006-11-19
Bad USB?...try plugging into the USB port where the flash drive is plugged in. You should know what the port is by previous fdisk -l. I don't know if it will help, but try looking at:
```
cat /etc/fstab
```

---

### Post by ridgeback on 2006-11-19
It doesn't come up when I plug it into any of the usb ports I have, and the flash drive is recognized when plugged into all of them.  Here is the fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=384677ac-fb20-4cc1-9bdb-098a5569a899 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=50e0f50b-2bae-498b-9677-e2b9994ac469 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


It doesn't look like the flash drive is there, even though I'm using one of its files as we speak.  Also of note is that I have no floppy drive.  Don't really know what's going on...

---

### Post by ReaderRat on 2006-11-19
Where is 'hda'? What sort of drive setup do you have?

---

### Post by ridgeback on 2006-11-19
hda is the master internal hard drive that I only use when I boot in windows, which could be why it isn't showing up.  hdb is the slave hard drive that boots linux.

---

### Post by ReaderRat on 2006-11-19
I am a bit of a newbie, so I'm out of questions. One thing I did not try, go to the top of the page and click on "Tags", then enter the word - external - in the search bar. I am sure you will get a lot of hits.

---

### Post by ridgeback on 2006-11-20
Solved! and I feel like an idiot...  It was getting enough power, but the power button wasn't turning the light off like it should, so I manually cut the power, and upon restart it was detected fine.  I suppose it was powered up from the minute I installed ubuntu, which must have been the issue.  Sorry for the headache...

---

