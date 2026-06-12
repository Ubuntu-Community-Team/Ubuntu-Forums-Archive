---
title: "Second hard drive troubles"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by yonexFactory on 2007-04-11
Hey, I'm trying to get my second hard drive to work with Ubuntu, but I'm afraid of doing something that will totally erase all of my music, movies, etc. on it. Can anyone help me?

Thanks

---

### Post by taurus on 2007-04-11
You probably need to mount it first before you can access it.  What's the output of this command from a terminal?

```
sudo fdisk -l
```
Otherwise, read this guide on how to mount it.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by annda on 2007-04-11
EDIT: i misunderstood the post so nothing here.

---

### Post by zvacet on 2007-04-11
You have to be more specific if you want to recive good help,advice,giude...What is o your first HD?How much space is free on the second HD?
[http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot]("http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot")
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

On the second link you will find how to install.

---

### Post by yonexFactory on 2007-04-12
Well, I'm dual-booting from my first hard drive (Ubuntu and XP) and I originally set up my second hard drive via XP. Basically what I want to do is be able to access my second hard drive from both Ubuntu and XP because that's the drive I've where got all my music, movies, documents, etc. That's why I said I'd like to be able to do this without completely wiping out my second hard drive.

Here's the output of sudo fdisk -l: 

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3966    31856863+   7  HPFS/NTFS
/dev/hda2            3967        9491    44379562+  83  Linux
/dev/hda3            9492        9729     1911735    5  Extended
/dev/hda5            9492        9729     1911703+  82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       24321   195358401    7  HPFS/NTFS


Sorry for the vague-ness and thanks again.

---

### Post by taurus on 2007-04-12
So you want to mount /dev/hdb1 in Ubuntu.  Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
```
Save the change.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```
And if you intend to write to /media/hdb1 (ntfs filesystem), then you need to use ntfs-3g instead of ntfs.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by yonexFactory on 2007-04-12
Thanks for all the help guys, I've got it working now. :D

---

