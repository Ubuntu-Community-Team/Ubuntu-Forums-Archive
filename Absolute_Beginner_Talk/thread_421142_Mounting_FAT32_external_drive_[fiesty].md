---
title: "Mounting FAT32 external drive [fiesty]"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-04-24
How would I go about this? I've tried adding this to the fstab

```
/dev/sdd /media/windows vfat umask=0000
```

but I get this error

```
root@glasgowm-desktop:/home/glasgowm# sudo mount /dev/sdd
mount: wrong fs type, bad option, bad superblock on /dev/sdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

then when I do a dmesg | tail I get this

```
root@glasgowm-desktop:/home/glasgowm# dmesg | tail
[48586.367155] sdd: Write Protect is off
[48586.367164] sdd: Mode Sense: 27 00 00 00
[48586.367167] sdd: assuming drive cache: write through
[48586.367173]  sdd: sdd1
[48586.391258] sd 6:0:0:0: Attached scsi disk sdd
[48586.391347] sd 6:0:0:0: Attached scsi generic sg5 type 0
[49043.350346] FAT: invalid media value (0x06)
[49043.350356] VFS: Can't find a valid FAT filesystem on dev sdd.
[49136.776036] FAT: invalid media value (0x06)
[49136.776044] VFS: Can't find a valid FAT filesystem on dev sdd.

```

---

### Post by joft on 2007-04-24
/dev/sdd represents the whole drive (with master boot sector). The log output you posted indicates (line 4), that there is one partition /dev/sdd1 . That's the one you have to use in /etc/fstab.

---

### Post by auraithx on 2007-04-24
Modified the fstab and now I get this

```
glasgowm@glasgowm-desktop:~$ sudo mount /dev/sdd1
mount: special device /dev/sdd1 does not exist

```

---

### Post by tomcheng76 on 2007-04-24
please post your "sudo fdisk -l"

---

### Post by joft on 2007-04-24
> **auraithx said:**
> Modified the fstab and now I get this

```
glasgowm@glasgowm-desktop:~$ sudo mount /dev/sdd1
mount: special device /dev/sdd1 does not exist

```

Your external FAT32 drive, is it a USB device? Then the device node changes with every plug-out and plug-in again.

I am not 100% sure, but you could use the UUID method instead of specifing a device node (/dev/xxx). So, plug-in your drive, find out which device node it has (e.g. by looking at syslog), then
```

ls -l /dev/disk/by-uuid

```
and pick the UUID of your external drive and enter it in /etc/fstab instead of the device node, but see "man fstab" first! AFAIK this should work.

---

### Post by auraithx on 2007-04-24
Woo, thanks guys. Yeah, it had changed to sdc.

Just using it once so that I can move all files from my filesystem (NTFS) [read-only] to this then format it, and move them back.

Should I format the filesystem hard drive in ext3 or fat32 ?

Thanks.

---

### Post by tomcheng76 on 2007-04-24
it depends on what do you like more
i will personally keep on what original filesystem it is
if you have windows installed, fat32 may be a good choice, although there are 3rd party driver for reading and writing the ext3
if Ubuntu Linux is the only OS you have, then both are more or less the same
However, if you choose ext3, you do not need to worry about the fregmentation inside the harddrive

---

### Post by auraithx on 2007-04-24
Cheers. I've seen the light and Ubuntu has been my only OS for a few months now.

ex3 it is.

---

### Post by joft on 2007-04-24
> **tomcheng76 said:**
> if Ubuntu Linux is the only OS you have, then both are more or less the same

Sorry, but this is wrong with big letters, bold and underlined.

FAT32 is a very simple and old filesystem. The core of it, the FAT was designed (AFAIK) in the 80's by bad&evil M$ . FAT32 is just a try to be compatible with the old M$-DOS and be able to use big disk/partitions and long filenames - nothing special, no features, easily breakable .... simply a "no go".

ext3 is a journaling filesystem (!) and extension to ext2. It's a "Unix"/POSIX filesystem, it follows a completely different approach (inodes), you have the concept of owners and access attributes and much more .... multitasking, multiuser capable.

So, please, don't say, that they are the same.

---

