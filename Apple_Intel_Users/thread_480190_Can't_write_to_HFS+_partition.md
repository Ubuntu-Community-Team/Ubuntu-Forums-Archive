---
title: "Can't write to HFS+ partition"
date: 2007-06-21
forum: Apple Intel Users
---

### Post by Ubivetz on 2007-06-21
Hi All!

I'm using Feisty AMD 64 on iMac and yesterday I had updated my system with Adept Updater.
But today I can't write to my HFS+ partition even by root! I.e
```

$ sudo bash
# cd /mnt/Macihtosh_HD
# mkdir 1

```
The system claims that my Mac partition is read-only one!
Now look at my /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda3
UUID=f48fb958-8848-4df9-bcdc-cc1c97d3a551 / reiserfs nouser,notail,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda4
UUID=01f442fe-8fc0-40a8-beed-2d61ae907e1d none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda2 /mnt/Macihtosh_HD auto users,atime,auto,rw,nodev,exec,suid 0 0

```

---

### Post by Gen2ly on 2007-06-21
Perhaps you need to check HFSfs because the fstab seems ok.  Heres the line I use:

```
/dev/sda2          /mnt/OSX         hfsplus  ro,exec,noauto,users                    0      0
```

As root you should be able write to it.  If you still are not able to I wrote this [[COLOR="Sienna"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2346494#post2346494") on checking hfsplus in ubuntu, possibly that will help.

---

### Post by Ubivetz on 2007-06-21
> **Dirk.R.Gently said:**
> Perhaps you need to check HFSfs because the fstab seems ok.  Heres the line I use:

```
/dev/sda2          /mnt/OSX         hfsplus  ro,exec,noauto,users                    0      0
```

As root you should be able write to it.  If you still are not able to I wrote this [[COLOR="Sienna"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2346494#post2346494") on checking hfsplus in ubuntu, possibly that will help.
I could write my HFS partition **before recent update**. ](*,)

---

### Post by Ubivetz on 2007-06-21
I just rebooted it OS X
perform 
```

diskutil disableJournal 

```
**ONCE AGAIN** and all became OK. I have no idea, why I must disable journalling many times.

---

### Post by kzm. on 2007-06-21
i know saw and wrote down three different fsab-endings.

user,rw 0 0 
rw,exec,auto,users 0 0
ro,exec,noauto,users 0 0

can anybody explain the differences and benfits of the approaches?

---

### Post by Gen2ly on 2007-06-21
zero problems.  first off:

rw and ro - read/write and read/only
exec - executable?  allow binaries to run?
users - Linux has got groups you need to be part of this to access different partitions.
auto and noauto - strangely this is the one that is confusing.  For me the disk will mount on either one of them, in whatever you have it set up as (e.g. /mnt/OS X) but auto will not mount in on the desktop but noauto will.

---

### Post by ivesjd on 2007-06-21
Thanks for that Dirk, Its nice to know about auto and noauto :)

---

### Post by Ubivetz on 2007-06-22
I have found that I can write to HFS+ partition when I boot in OS X and then reboot to Linux.
I have the following in /var/log/dmesg:
```

[   55.880556] hfs: Filesystem was not cleanly unmounted, running 
fsck.hfsplus is recommended.  mounting read-only.

```
I think it is defintely bug and I want to submit bug report but I don't know how.

P.S. Where can I get fsck.hfsplus?

---

### Post by Ubivetz on 2007-06-22
I tried to fix partition:
```

root#  hpfsck /dev/sda2
*** Checking Volume Header:
Volume was not cleanly unmounted
Volume is inconsistent

Invalid total blocks 18C8B00, expected 
0                                                Done ***
*** Checking Backup Volume Header:
Unexpected Volume signature '  ' expected 'H+'
hpfsck: hpfsck: This is not a HFS+ volume (Unknown error 
18446744073709551615)

```

---

### Post by Gen2ly on 2007-06-22
Best probably to use this:

[**[COLOR="Sienna"]HowTo check and repair an HFSplus drive/partition in Ubuntu[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=392287")

---

### Post by ronocdh on 2007-06-22
> **Dirk.R.Gently said:**
> Best probably to use this:

[**[COLOR="Sienna"]HowTo check and repair an HFSplus drive/partition in Ubuntu[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=392287")
We need stickies, damn it! Even if they all are belong to Dirk for great justice! (OK, Trouble1313 just posted a sweet one, but still.)

---

### Post by thegnu on 2008-04-13
> **Dirk.R.Gently said:**
> auto and noauto - strangely this is the one that is confusing.  For me the disk will mount on either one of them, in whatever you have it set up as (e.g. /mnt/OS X) but auto will not mount in on the desktop but noauto will.
It's been a year since you wrote this, but auto and noauto are about mounting at boot time.

The automounting when you plug in a drive is handled by other applications.  In Arch Linux, I have automounting set up using HAL, udev rules, and AutoFS.  I don't know how Ubuntu does it, but having auto in fstab won't automount something while the system's up, only on boot.

Cheers.
-Nathan

---

