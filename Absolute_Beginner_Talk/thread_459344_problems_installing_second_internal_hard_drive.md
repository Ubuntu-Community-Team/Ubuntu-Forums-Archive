---
title: "problems installing second internal hard drive"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by hipmo on 2007-05-30
hi-

i've looked at several posts on this topic, and i've tried what everyone has suggested, so i must be missing something.  also, i'm super new at linux, using kubuntu feisty with KDE 3.5.6.

i'm trying to get it so that i can access the second hard drive through konqueror, but it's not mounting properly i guess:
> 
w@w-desktop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

then dmesg | tail says:

> w@w-desktop:~$ dmesg | tail
[ 1994.935855] kjournald starting.  Commit interval 5 seconds
[ 1994.936054] EXT3-fs: mounted filesystem with ordered data mode.
[ 2005.113913] VFS: Can't find ext3 filesystem on dev hdb.
[ 2408.199275]  hdb: hdb1
[ 2410.213144]  hdb: hdb1
[ 2549.520843]  hdb: hdb1
[ 2551.592252]  hdb: hdb1
[ 2582.810048]  hdb: hdb1
[ 2584.854889]  hdb: hdb1
[ 2638.910152] VFS: Can't find ext3 filesystem on dev hdb.

i used qtparted to create and format the partition hdb1.

when i use fdisk and use the w command: 
> 
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.


and then two windows pop up, each saying 
> 
a new medium has been detected.  what do you want to do?
medium type: unmounted hard disk volume

open in new window
do nothing

when i attempt to open in new window, nothing happens.


my fstab looks like this:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=839969f0-3a58-429e-8835-2a3e98f0d8a1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1d9c34e6-5875-461e-83d5-f7637a26a640 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb        /media/storage  ext3    rw,umask=0000,user,gid=users        0       0




i am at a complete loss.  any help would be awesome!!!  thanks!

---

### Post by taurus on 2007-05-30
Shouldn't it be

```
/dev/hdb[COLOR="Blue"]**1**[/COLOR] /media/storage ext3 rw,umask=0000,user,gid=users 0 0
```
Otherwise, post the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by Inxsible on 2007-05-30
What have you formatted /dev/hdb1 as ? EXT3 ?
 
your fstab says its already mounted at /media/storage. 
 
change that line to this. Make sure you back up your files before changing
```
 /dev/hdb1 /media/storage ext3 rw,umask=0000,user,gid=users 0 0

```

---

### Post by Inxsible on 2007-05-30
taurus, you really are quick !!!!!!!
 
I am thinking conspiracy again ;)

---

### Post by hipmo on 2007-05-30
> **taurus said:**
> Shouldn't it be

```
/dev/hdb[COLOR="Blue"]**1**[/COLOR] /media/storage ext3 rw,umask=0000,user,gid=users 0 0
```
Otherwise, post the output of this command from a terminal.

```
sudo fdisk -l
```


here's the output 

> Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7205    57874131   83  Linux
/dev/hda2            7206        7297      738990    5  Extended
/dev/hda5            7206        7297      738958+  82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
16 heads, 63 sectors/track, 158816 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1      146366    73768432+  83  Linux


and yes, i formatted hdb1 as ext3.

thanks, i changed that line, but it still says 

> 
w@w-desktop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


and thanks for your help.

---

### Post by taurus on 2007-05-30
> **Inxsible said:**
> 
I am thinking conspiracy again ;)

Maybe, maybe not.  :-$

---

### Post by taurus on 2007-05-30
> **hipmo said:**
> here's the output 

and yes, i formatted hdb1 as ext3.

thanks, i changed that line, but it still says 

and thanks for your help.

Do you have anything on /dev/hdb1 that you need to save right now?

Also, I would suggest you make an entry in /etc/fstab for /dev/hdb1 like

```
/dev/hdb1   /media/storage   ext3   defaults   0   1
```
And if you want to have a write permission to /media/storage, just change the ownership of /media/storage from root to your login name, _assuming_ it's **hipmo**.

```
sudo chown -R **hipmo**:**hipmo** /media/storage
```

---

### Post by Inxsible on 2007-05-30
Boot from the Live CD and perform a 
```
sudo fsck /dev/hdb1
```
 
and try again.

---

### Post by Inxsible on 2007-05-30
Your hdb1 also has a boot flag, Do you have another version of Linux installed on it ?

---

### Post by hipmo on 2007-05-30
> **taurus said:**
> Do you have anything on /dev/hdb1 that you need to save right now?

Also, I would suggest you make an entry in /etc/fstab for /dev/hdb1 like

```
/dev/hdb1   /media/storage   ext3   defaults   0   1
```
And if you want to have a write permission to /media/storage, just change the ownership of /media/storage from root to your login name, _assuming_ it's **hipmo**.

```
sudo chown -R **hipmo**:**hipmo** /media/storage
```


no, nothing i need to save. i made those changes, and this happened:
> 
w@w-desktop:~$ sudo mount -a
mount: special device dev/hdb1 does not exist





also, what does 

```
sudo fsck /dev/hdb1
```

do?

as for the bootflag, actually there it has mandrake 10 on it - i could never get it to work.  it used to be a dual boot mandrake/XP drive, but i want to make the whole thing accessible to kubuntu so i can use it for storage. thanks!

---

### Post by Inxsible on 2007-05-30
So if you dont need to save the Mandrake, why not put in your LiveCD and just format the drive completely.
 
fsck checks the file system and reports if there are issues with it

---

### Post by taurus on 2007-05-30
```
sudo mke2fs -j /dev/hdb1
sudo mount -a 
df -h
```

---

### Post by hipmo on 2007-05-30
ok, so i'm not sure what changed, but i just tried using the live cd and for some reason it wasn't working. whatever.  i booted back to linux (hda), and now apparently hdb is working.  i can access it through konqueror at /media/storage, it's mounted, it shows up on ```
mount 
```and on ```
fdisk -l
```, and it seems all is well.  i didn't do the last thing that you suggested, taurus, i was going to once the system booted back up, but it seems like everything is fine.  thanks for your help!  what do you guys think it was that actually made it work?  was it just a matter of rebooting after changing the fstab line to```
 /dev/hdb1 
```?  anyway, thanks a bunch, i really appreciate it.

---

### Post by Inxsible on 2007-05-30
> **hipmo said:**
> was that actually made it work? was it just a matter of rebooting after changing the fstab line to```
 /dev/hdb1 
```? 
 
Not necessarily, if you did a mount -a (which remounts all the drives in the fstab) it should have worked too. Linux is better than Windows for the very fact that you do not have to reboot every time you make a small change !!

---

### Post by CityofAsh on 2007-05-30
Well this worked for me. I make one full logical partition ext3 on the hdb1. Also create a folder in /mnt  i made mine /mnt/hdb
now to mount
```
sudo mount -t auto /dev/hdb1 /mnt/hdb 
```

must be root to mount.
See if that works for ya.

---

