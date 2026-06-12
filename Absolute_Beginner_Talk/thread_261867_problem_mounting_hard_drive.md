---
title: "problem mounting hard drive"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by comicus on 2006-09-20
I've been trying to mount a 200gb hard drive I just put into my system, but I'm having some trouble.

When I try to mount it, i get the following:

john@Jupiter:~$ sudo mount -t ext3 /dev/hdd1 /media/hdd1
mount: wrong fs type, bad option, bad superblock on /dev/hdd1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

so i did an fdisk -l and it gave me:

Disk /dev/hdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       24792   199141708+  83  Linux

I'm a total newb, but that looks okay to me...

So i try to run an fsck on it:

fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/hdd1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

So i try the e2fsck thing, and it says the same thing...:

john@Jupiter:~$ sudo e2fsck -b 8193 /dev/hdd1
e2fsck 1.38 (30-Jun-2005)
e2fsck: Bad magic number in super-block while trying to open /dev/hdd1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

Any ideas on how i can get this drive mounted? I don't care if i lose all the info, if that makes it easier, its only a blank drive. And we had a power outage this morning, but everything else seems okay, and i didn't even try to mount it till after the outage, so i'm not sure that has anything to do with it.

Thanks in advance for any help :)

-comicus

---

### Post by catlett on 2006-09-20
Go to System<Administration<Gnome partition editor that is the gnome partitioner gparted. If for some reason it isn't installed enter ```
sudo apt-get install gparted 
```
Enter into the app and select the drive from the drop down box. Delete the partition (if it is only one partition that will take care of the whole drive). Select 'new' and make it a primary, ext3 partition. Make sure to hit apply.
Then reboot and try mounting. See if it gives the badblock era again.

---

