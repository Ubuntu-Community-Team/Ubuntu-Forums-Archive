---
title: "Help on mounting FAT on Ubuntu"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by absolutnoob on 2007-05-27
Hi, I have installed Ubuntu 6.06 on my computer couple days ago. I have two seperate hard drives and dual boots to Windows 98 (80GB) and Ubuntu (300GB). When I boot into Ubuntu, I could not mount the Window's hard drive to Ubuntu. I would really be appreciated if someone can help me.

---

### Post by taurus on 2007-05-27
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Otherwise, post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by %hMa@?b&lt;C on 2007-05-27
sudo mount -o loop /path/to/where/you/want/it/mounted /dev/harddrivename (it could be hdc or hda or sdb or whatever)

---

### Post by absolutnoob on 2007-05-27
Thanks for the advice, I followed the instruction on the link you've gave me, still, I cannot get my hard drive mounted, and this is what is shown after I typed "sudo disk -l"


Disk /dev/hda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       36293   291523491   83  Linux
/dev/hda2           36294       36481     1510110    5  Extended
/dev/hda5           36294       36481     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1738    13960453+   c  W95 FAT32 (LBA)
/dev/hdb2            1739        9732    64211805    f  W95 Ext'd (LBA)
/dev/hdb5            1739        9732    64211773+   b  W95 FAT32
david@david-desktop:~$

---

### Post by gn2 on 2007-05-27
Go to [www.getautomatix.com](www.getautomatix.com) install Automatix, and use the Auto-Mounter listed in Miscellaneous.

It auto-mounts Fat32 and NTFS drives/partitions and makes them writeable. Automatically.

---

### Post by taurus on 2007-05-27
> **absolutnoob said:**
> Thanks for the advice, I followed the instruction on the link you've gave me, still, I cannot get my hard drive mounted, and this is what is shown after I typed "sudo disk -l"


Disk /dev/hda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       36293   291523491   83  Linux
/dev/hda2           36294       36481     1510110    5  Extended
/dev/hda5           36294       36481     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1738    13960453+   c  W95 FAT32 (LBA)
/dev/hdb2            1739        9732    64211805    f  W95 Ext'd (LBA)
/dev/hdb5            1739        9732    64211773+   b  W95 FAT32
david@david-desktop:~$

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```
/dev/hdb1   /media/hdb1   vfat   iocharset=utf8,umask=000   0   0
/dev/hdb5   /media/hdb5   vfat   iocharset=utf8,umask=000   0   0
```
Save it.  Then, create two new mount points and mount them.

```
sudo mkdir /media/hdb1 /media/hdb5
sudo mount -a
df -h
```

---

### Post by absolutnoob on 2007-05-27
Thank you for the help, Tauras, now my FAT hard drives is mounted and works!

---

