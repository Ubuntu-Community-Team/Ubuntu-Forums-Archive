---
title: "Accessing hard drive with ubuntu?"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by lirael on 2006-12-07
I have two hard drives on my computer; one of them is ntsc formatted and has all of my mp3s and various other media files on it. I installed ubuntu on the second hard drive but once I did, the first hard drive didn't even show up in Places>Computer. How do I get it to show up, and even if I do that will I be able to access (and use) the files? I would like to run on Ubuntu alone (leaving Windows XP behind) while keeping my files from the first hard drive.

---

### Post by taurus on 2006-12-07
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by bodhi.zazen on 2006-12-07
taurus:

Stop it ! You are taking all the fun out of writing long, poorly written "how to mount and edit fstab" for new users :p

My typing skills are going to atrophy :(

---

### Post by taurus on 2006-12-07
> **bodhi.zazen said:**
> taurus:

Stop it ! You are taking all the fun out of writing long, poorly written "how to mount and edit fstab" for new users :p

My typing skills are going to atrophy :(
Oh well...  :oops:  #-o

---

### Post by lirael on 2006-12-07
Okay, I'm having problems. This is what I get when I put in the "sudo fdisk -l" command:

> Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9777    78533721   83  Linux
/dev/hda2            9778        9964     1502077+   5  Extended
/dev/hda5            9778        9964     1502046   82  Linux swap / Solaris

Disk /dev/hdb: 33.8 GB, 33820286976 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4111    33021576    7  HPFS/NTFS



but when I try to put in "/dev/hdb1" with the suggested permissions into "etc/fstab" and try to mount it I get errors. Furthermore, "/dev/hdb1" doesn't even show up in "etc/fstab". This is my original "etc/fstab":

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8e1f9fb6-540c-4a95-8de6-4c4fcae345e3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=4e1b022a-6d47-417e-af3e-e961c4367fc8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


what do i need to do?

---

### Post by lirael on 2006-12-07
Anybody?

---

### Post by bodhi.zazen on 2006-12-07
to mount:

```
suod mkdir /media/windows
sudo mount -t ntfs /dev/hdb1 /media/windows
```

Add this to fstab:

```
sudo gedit /etc/fstab
```
> /dev/hdb1 /media/windows ntfs auto,users 0 0

If you want read-write access you should try [ntfs-3g](http://www.ubuntuforums.org/showthread.php?&t=217009)

---

### Post by Jay-Jay on 2006-12-07
...

---

### Post by lirael on 2006-12-07
Yay! It works now, thank you!

---

