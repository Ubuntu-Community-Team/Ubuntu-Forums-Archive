---
title: "Access multiple hard drives"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by g.off on 2007-04-29
I installed Xubuntu on a computer that previously had Windows on it and now I can't access two of my three hard drives. I completely formatted my drive with Windows on it and installed Xubuntu in its place and now I can't access my other two drives where I backed up some of my files prior to formatting my Windows drive.

I need help trying to use my other drives in Xubuntu and accessing the files on it.  Is there a way to do this?

---

### Post by taurus on 2007-04-29
You need to mount them before you can access them.

What's the output of this command from a terminal?

```
sudo fdisk -l
```
Or here is a guide.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by g.off on 2007-04-29
This is the output. What do I do now? I'm a new user to Linux and Xubuntu.

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4820    38716618+  83  Linux
/dev/hda2            4821        4865      361462+   5  Extended
/dev/hda5            4821        4865      361431   82  Linux swap / Solaris

Disk /dev/hdb: 4334 MB, 4334722560 bytes
255 heads, 63 sectors/track, 527 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         527     4233096    c  W95 FAT32 (LBA)

Disk /dev/hdd: 6448 MB, 6448619520 bytes
240 heads, 63 sectors/track, 833 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1         833     6297448+   c  W95 FAT32 (LBA)

---

### Post by taurus on 2007-04-29
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```

/dev/hdb1   /media/hdb1   vfat   iocharset=utf8,umask=000   0   0
/dev/hdd1   /media/hdd1   vfat   iocharset=utf8,umask=000   0   0

```
Save the changes.  Then, create two new mount points and mount them.

```
sudo mkdir /media/hdb1 /media/hdd1
sudo mount -a
df -h
```

---

