---
title: "Can't see XP partition to access music"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by jonnyboi303 on 2008-02-04
Hey all another n00b here.  So looking at the threads for people with similar problems, I couldn't find one that was the same as mine.  I'm running ubuntu 7.10 on my laptop and want to access my NTFS partition so that I can listen to the music and videos on there while using ubuntu.  Most people seem to be able to go into /media or whatever and see their NTFS drive with stuff in it.  My NTFS drive is on sda1, but when I go to /media/sda1 the folder is empty.  What am I suppose to do to be able to use amarok and stuff to play my music in ubuntu?

---

### Post by oedha on 2008-02-04
first....have you shutdown your winblows properly ?
next :==> sudo gedit /etc/fstab
is there any statement concerning to your /media/sda1
or maybe you can port the result of sudo fdisk -l

---

### Post by Mogurijin on 2008-02-05
I would make sure that Windows did shut down properly (even if it means booting back into it and shutting it down again). When Windows doesn't "properly" shut down (ie; hitting your power button) it continuous to have a death grip on it's drives, which means Ubuntu can't access them. Really annoying if you accidentally boot to Windows since you have to let it finish booting and then shut it down...

---

### Post by jonnyboi303 on 2008-02-07
ahhh such a n00b. thanks for the help

---

### Post by Sambie on 2008-02-08
I was able to gain access to my windows XP Pro partition drive on my Ubuntu but it seems now that it won't even recognize the partition. I tried shutting down windows and it still doesn't see it. 

As Unbuntu was loading it was doing a Fscan on Sda1 and it quickly started as soon as it was finish so I wasn't able to read it.

sudo fdisk -l results
Disk /dev/sda: 250.0 GB, 250059350016 bytes

255 heads, 63 sectors/track, 30401 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xc1ce8846



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1       14154   113691973+   7  HPFS/NTFS

/dev/sda2           14155       29739   125186512+  83  Linux

/dev/sda3           29740       30401     5317515    5  Extended

/dev/sda5           29740       30401     5317483+  82  Linux swap / Solaris


sudo gedit /etc/fstab results
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=261c39f6-a59d-4f44-bd0d-990f17efcff8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4728b2df-2c50-450f-8359-a92aff073498 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

How can I get my WinXP partition to show up again?

---

### Post by Rocket2DMn on 2008-02-08
Add to your fstab
```
gksudo gedit /etc/fstab
```
the line
```
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.utf8 0 0
```
Assuming the folder exists, you can then mount with
```
sudo mount -a
```

---

### Post by Sambie on 2008-02-08
Alright I've done what you said so my current settings are

> gedit /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=261c39f6-a59d-4f44-bd0d-990f17efcff8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4728b2df-2c50-450f-8359-a92aff073498 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1 /media/sda1 ntfs-3g defaults,locale=en_US.utf8 0 0

Heres what I recieve after i've enter sudo mount -a

> brittany@brittany-desktop:~$ sudo mount -a
fuse: failed to access mountpoint /media/sda1: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sda1 ()
mount: mount point gedit does not exist

---

### Post by Rocket2DMn on 2008-02-08
That's why I said "Assuming the folder exists".  You need to make the directory first
```
sudo mkdir /media/sda1
sudo mount -a
```
:)

---

### Post by Sambie on 2008-02-08
Heres the results from the terminal
> brittany@brittany-desktop:~$ sudo mkdir /media/sda1
[sudo] password for brittany:
brittany@brittany-desktop:~$ sudo mkdir /media/sda1
mkdir: cannot create directory `/media/sda1': File exists
brittany@brittany-desktop:~$ sudo mount -a
mount: unknown filesystem type ''
brittany@brittany-desktop:~$

---

### Post by Sambie on 2008-02-08
Thanks for the help Rocket2DMn ;)

---

