---
title: "[SOLVED] How to mount my winxp fat32 partition?"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2007-11-07
I decided to install both winxp and Ubuntu (6.06) on my laptop. I had heard that there might be difficulty if the windows partition was ntfs, so when it asked, I installed it as the fat32 filesystem. (My xp partition has my wireless disabled on it so when I am running XP I don't have security issues... I only go online while running Ubuntu.)
I have some files (.doc) on there that I need to be able to edit in Ubuntu (Open Office) so I can e-mail them. I cannot seem to figure out how to mount this partition. 

I have no clue as to where to start, so all the help I can get would be appreciated!

---

### Post by Pumalite on 2007-11-07
Post:

sudo fdisk -lu

---

### Post by Paul820 on 2007-11-07
You need ntfs-3g. Have a look in synaptic package manager.

---

### Post by Pumalite on 2007-11-07
You don't need ntfs-3g for vfat(fat32)

---

### Post by Paul820 on 2007-11-07
My bad, i should learn to read better :)

---

### Post by mrfelker on 2007-11-07
cd /media

Look what device windows is on - usually /dev/sda1 or /dev/hda1 - depends on your HD - SCSI or IDE.

Click on the device and you will see and be able to write to FAT32 with extra progs for NTFS.

Actually the volume should appear on your Desktop (if you label the Windows HD as Windows rather than leaving it blank the name will even appear.

But whatever you do don't mess with /etc/fstab.

If you just want to mount the Windows and not have it appear automatically:

sudo mount -t vfat /dev/sda1 /media/windows (you will need to mkdir /media/windows firts!

to umount -- sudo umount /media/windows (or you can just use /media/windows.

Hope this helps.

---

### Post by Papa-san on 2007-11-08
Here's sudo fdisk -su:

```
Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    14121134     7060536    c  W95 FAT32 (LBA)
/dev/hda2        14121135    37977659    11928262+  83  Linux
/dev/hda3        37977660    39070079      546210    5  Extended
/dev/hda5        37977723    39070079      546178+  82  Linux swap / Solaris
john@john-laptop:~$
```I really have no idea what I'm doing... LOL

It would be nice if this partition would be available on my desktop, however that is done!

I'm a lifer windows user who just cannot stand it anymore... Ubuntu is great for me because people who know what they are doing have made it usable for people like me who are clueless... Is making a directory that simple? Just mkdir and what I want it to be? This is where I stopped trying to use wine.

If it can be messed up, I'll do it QUICK! (Just ask azz. lol)

---

### Post by overdrank on 2007-11-08
> **Papa-san said:**
> Here's sudo fdisk -su:

```
Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    14121134     7060536    c  W95 FAT32 (LBA)
/dev/hda2        14121135    37977659    11928262+  83  Linux
/dev/hda3        37977660    39070079      546210    5  Extended
/dev/hda5        37977723    39070079      546178+  82  Linux swap / Solaris
john@john-laptop:~$
```I really have no idea what I'm doing... LOL

It would be nice if this partition would be available on my desktop, however that is done!

I'm a lifer windows user who just cannot stand it anymore... Ubuntu is great for me because people who know what they are doing have made it usable for people like me who are clueless... Is making a directory that simple? Just mkdir and what I want it to be? This is where I stopped trying to use wine.

If it can be messed up, I'll do it QUICK! (Just ask azz. lol)

HI this link may help.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
Good luck!

---

### Post by richiewrt on 2007-11-08
If you haven't tried this,  go Places---->computer

should see all your partitions in there. just right click, mount voume and it should show up

that is if it is there.

---

### Post by overdrank on 2007-11-08
> **richiewrt said:**
> If you haven't tried this,  go Places---->computer

should see all your partitions in there. just right click, mount voume and it should show up

that is if it is there.

Hi and please correct me If I am wrong but I do not think that is a option in dapper
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by Papa-san on 2007-11-08
> **richiewrt said:**
> If you haven't tried this,  go Places---->computer

should see all your partitions in there. just right click, mount voume and it should show up

that is if it is there.

It shows up,  but won't mount. Here's the error message I get:
```
error: device /dev/hda1 is not removable

error: could not execute pmount
```

---

### Post by Papa-san on 2007-11-08
When I do a makedir, do I do it as sudo? Or does it not matter?

---

### Post by overdrank on 2007-11-08
> **Papa-san said:**
> When I do a makedir, do I do it as sudo? Or does it not matter?

HI  I doubt it will work without sudo. :KS

---

### Post by Papa-san on 2007-11-08
Thanks.
I got it as soon as I tried.
However, this is what I got:```
john@john-laptop:~$ mkdir /media/windows
mkdir: cannot create directory `/media/windows': Permission denied
john@john-laptop:~$ sudo mkdir /media/windows
Password:
john@john-laptop:~$ gksudo gedit /etc/fstab

(gedit:12941): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
john@john-laptop:~$ sudo mount -a
mount: mount point  does not exist
mount: mount point  does not exist
mount: mount point  does not exist
mount: mount point  does not exist

```This is (now) fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
    *

      /dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

    *

shortname=mixed
user=user,group=group

```
Maybe using gksudo was a problem?

---

### Post by Pumalite on 2007-11-08
suso mkdir /media/vfat
sudo mount -t vfat /dev/hda1 /media/vfat

---

### Post by Papa-san on 2007-11-08
Thank you very much, sir!
I am now able to do exactly what I had hoped to do!
I'll mark this one as solved!:KS

---

### Post by Pumalite on 2007-11-08
You are welcome. Good luck.

---

