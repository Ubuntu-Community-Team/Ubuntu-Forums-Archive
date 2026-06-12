---
title: "Can't mount NTFS drive"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by Zero Ziat on 2008-03-31
[IMG]http://i20.photobucket.com/albums/b215/Ziat/error.png[/IMG]

That's what I get when I try to mount my Windows partition, which is kinda broken for some odd reason (some iPod fun) probably off these forums. (Bootup, restart. =/) So I fell into Ubuntu, as a backup OS and planned to backup my files from my Windows partition, format it and reinstall, since it works better than Wine itself.

**Off-Topic**
Practically when I also try to repair Windows XP, I put in the CD, but I see the partition is not recognized as NTFS, so it's all like messed up.

Help?

---

### Post by lisati on 2008-03-31
Are you getting the error when you try to boot with Windows?

---

### Post by Zero Ziat on 2008-03-31
Nope, I get it when I try to mount the NTFS drive (Windows) with the uhh, Nautilus is it? Thingy, like, Right-click, Mount Volume.

Hope I helped.

---

### Post by Zero Ziat on 2008-03-31
Uhh, hello?

---

### Post by Inxsible on 2008-03-31
can you post the output of the following commands```
sudo fdisk -l
```-l is lowercase L and```
df -h
```and finally ```
cat /etc/fstab
```

---

### Post by Tom--d on 2008-03-31
I did this to mount my NTFS extrenal hard drive.

```
sudo mount -t ntfs-3g /dev/sdb1 /media/Network -o force
```
It might help :\
Change the /dev/sdb1 to your one and /media/Network. (just look in those directories)

---

### Post by Zero Ziat on 2008-03-31
Tom--d:
> nano@Nano:~$ sudo mount -t ntfs-3g /dev/hda1 /media/ -o force
Unexpected clusters per mft record (-1).
Failed to mount '/dev/hda1': Invalid argument
The device '/dev/hda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

Inxsible: 
> nano@Nano:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e2e8931

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3795    30483306    7  HPFS/NTFS
/dev/hda2            3796        3847      417690    f  W95 Ext'd (LBA)
/dev/hda3            3848        4865     8177085   83  Linux
/dev/hda5            3796        3847      417658+  82  Linux swap / Solaris

> nano@Nano:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e2e8931

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3795    30483306    7  HPFS/NTFS
/dev/hda2            3796        3847      417690    f  W95 Ext'd (LBA)
/dev/hda3            3848        4865     8177085   83  Linux
/dev/hda5            3796        3847      417658+  82  Linux swap / Solaris

> nano@Nano:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=b64a97d8-94dd-4e58-928b-d6564dbb23e9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=b39edcbb-6091-4e5e-b087-04dd4d209a16 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
nano@Nano:~$ |


---

### Post by bred on 2008-03-31
> **Zero Ziat said:**
> [IMG]http://i20.photobucket.com/albums/b215/Ziat/error.png[/IMG]

That's what I get when I try to mount my Windows partition, which is kinda broken for some odd reason (some iPod fun) probably off these forums. (Bootup, restart. =/) So I fell into Ubuntu, as a backup OS and planned to backup my files from my Windows partition, format it and reinstall, since it works better than Wine itself.

**Off-Topic**
Practically when I also try to repair Windows XP, I put in the CD, but I see the partition is not recognized as NTFS, so it's all like messed up.

Help?

[COLOR="Blue"]I had the same problem and I tried to unmount correctly(to remove safe) from windows and only then it worked correctly on ubuntu
hope it help[/COLOR]

---

### Post by Zero Ziat on 2008-03-31
nano@Nano:~$ sudo umount /dev/hda1
umount: /dev/hda1: not mounted

---

### Post by Tomatz on 2008-03-31
Put your xp install disk in, when it finishes loading press **R** to enter the **recovery console** when the (crappy) xp recovery console loads type **chkdsk /r** That should repair the ntfs partition.

I always find chkdsk best for ntfs unfortunatly :(

---

### Post by Zero Ziat on 2008-04-01
Dude, I totally FORGOT about that, thank you a real lot, man!

I'm changing topic title to SOLVED and thanking everyone for their efforts.

---

