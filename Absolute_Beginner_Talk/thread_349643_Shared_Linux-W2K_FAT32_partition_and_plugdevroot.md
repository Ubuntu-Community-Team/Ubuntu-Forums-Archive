---
title: "Shared Linux-W2K FAT32 partition and plugdev/root"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Phrawm48 on 2007-01-30
On my W2K Pro / Ubuntu 6.01 dual-boot computer, I've created a FAT32 partition which I intend to use to share email files, browser bookmarks, and other stuff that I want to keep in sync between the two o.s.'s.  The FAT32 partition mounts automatically ( /dev/hda8 ) and I can generally read from and write to it without difficulty.

When the drive gets mounted, the group=plugdev and the owner=root.  The group / owner thing still confuses me a bit.  Is this best, or should I  configure the drives so that, for example:

[LIST]
[*]Something else becomes the group?

[*]My user account becomes the owner?
[/LIST]

Cheers & thanks,
Ric
SFO

---

### Post by taurus on 2007-01-30
Your login name should be the owner and group of that partition/drive.

---

### Post by Phrawm48 on 2007-02-03
Per the preceding post in this thread, I'm trying to change the owner-group of the aforementioned FAT32 partition to my login name but can't figure out how best to proceed.

Here's my *fstab* file at the time of login.

> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /boot           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda8       /media/hda8     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


I then use the following commands to make the dev/hda8 partition accessible as XFER.

> sudo mkdir /media/XFER
sudo mount -t vfat /dev/hda8 /media/XFER -o iocharset=utf8,umask=000


After doing so, I can use *ls /media/XFER* to view the directories and files on the FAT32 partition.   Doing so shows that  all directories and files have *root*-*plugdev* as the owner-group of both the partition as well as all directories and files contained in it.

What I _cannot_ at this point do is use *sudo chown -R * or *sudo chgrp* to change XFER's owner-group to my login name.   If I try to do this, I receive an "Operation not permitted" message for every sub-directory and file on the FAT 32 partition.

My hunch is that the answer lies in editing /etc/fstab, probably the *umask* and *uid* options, but I don't want to start changing these experimentally lest I really break something.

With than in mind, can someone please suggest the best way to make my login name the owner-group of */media/XFER* ( nee /media/hda8 )?

(By the way, when making that change, is there also a simple way to eliminated the need to prefix XFER with */media/*?)

Cheers & thanks,
Ric
SFO

---

### Post by Phrawm48 on 2007-02-04
Aha - I just found out that if one can run the KDE desktop in addition to Gnome (I almost always run Gnome), that KDE has a GUI tool that allows you to change the settings in */etc/fstab*.  More specifically, I changed the entry for */dev/hda8* to:
> 
/dev/hda8 /media/hda8 vfat defaults,utf8,umask=007,uid=1000,gid=1000,auto,rw,users 0 1

This not only fixed my immediate problem, it helped me see how the changes appear in *fstab*.

Cheers & hope this helps,
Ric
SFO

---

