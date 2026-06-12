---
title: "Disk Mount Daemon?"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by Nachtengel on 2006-02-02
Hello all,

Just some quick help needed, I have a 2nd hard drive I'm trying to mount, but I keep getting strange errors when I try and mount it. It works some times & doesn't other times.

target hard drive: /dev/hdb/home/user/folder
target mount point: ~/folder

when I enter:

$ sudo mount -t ext3 /dev/hdb/home/user/folder /mnt/secondary/
Password:
mount: special device /dev/hdb/home/user/folder does not exist
       (a path prefix is not a directory)

$ sudo mount -t ext3 /dev/hdb /mnt/secondary/
mount: /dev/hdb already mounted or /mnt/secondary/ busy

$ ls -a /mnt/secondary
.  ..

I've tried editing it into my fstab and mtab:

from fstab:
#new mount
/dev/hdb/home/user/folder	/home/targetuser/targetfolder	ext3	defaults, errors=remount-rw	0	1

from mtab:
#new mount
/dev/hdb/home/user/folder	/home/targetuser/targetfolder	ext3	defaults, errors=remount-rw	0	1

still can't access anything though.

Is there a daemon I have to restart in order to apply the changes in fstab & mtab?  Any glarring errors in my process?

---

### Post by heimo on 2006-02-02
[quote=Nachtengel]
$ sudo mount -t ext3 /dev/hdb/home/user/folder /mnt/secondary/
Password:
mount: special device /dev/hdb/home/user/folder does not exist
       (a path prefix is not a directory)

$ sudo mount -t ext3 /dev/hdb /mnt/secondary/
mount: /dev/hdb already mounted or /mnt/secondary/ busy
[/quote] 
Your device names are incorrect. In most cases, it should be something like /dev/hdb1 (where 1 is partition number), or it could be hda/b/c/d, sda/b/c/d..

List your partitions using command:
```
sudo fdisk -l /dev/hdb

``` See if some of those are already mounted:
```
mount

```

[quote=Nachtengel]Is there a daemon I have to restart in order to apply the changes in fstab & mtab?
[/quote] 
No need to restart anything, but you still need to mount the partitions. Only edit fstab file, leave mtab alone. :)

---

### Post by Nachtengel on 2006-02-03
Ok, it's hdb1

$ mount /dev/hdb1/home/nachtengel/music
[mntent]: line 9 in /etc/fstab is bad
mount: can't find /dev/hdb1/home/user/folder in /etc/fstab or /etc/mtab

the line in question now reads

/dev/hdb1/home/user/folder /home/targetuser/targetfolder  ext3    defaults, errors=remount-rw     0       1

it's clearly in fstab... so now what?

---

### Post by cwaldbieser on 2006-02-03
[QUOTE=Nachtengel]Ok, it's hdb1

$ mount /dev/hdb1/home/nachtengel/music
[mntent]: line 9 in /etc/fstab is bad
mount: can't find /dev/hdb1/home/user/folder in /etc/fstab or /etc/mtab

the line in question now reads

/dev/hdb1/home/user/folder /home/targetuser/targetfolder  ext3    defaults, errors=remount-rw     0       1

it's clearly in fstab... so now what?[/QUOTE]

You can only mount the filesystem on the device at its root-- not at some arbitrary directory in the filesystem.  Change the line to
```

/dev/hdb1 /home/targetuser/targetfolder  ext3    defaults, errors=remount-rw     0       1

```

---

### Post by Sutekh on 2006-02-03
Ignore this one.

---

