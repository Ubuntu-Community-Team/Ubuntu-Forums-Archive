---
title: "mounting question"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by spookyct on 2007-06-05
I installed Kubuntu yesterday...  and after that I have lost the mount to my windows partitions.

can someone help me get those back?

This is a screenshot of the error message.

---

### Post by taurus on 2007-06-05
Can you post the output of this command from a terminal?

```
sudo fdisk -l
```
Otherwise, here's a guide, [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows).

---

### Post by mahiyar on 2007-06-05
Mounting drives has been a typical problem in KDE, that's why in spite of excellent programmes in KDE I moved over to gnome based distro.

---

### Post by spookyct on 2007-06-05
Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1958    15727603+   7  HPFS/NTFS
/dev/hda2            1959        7475    44315302+   f  W95 Ext'd (LBA)
/dev/hda5            2612        7475    39070048+   7  HPFS/NTFS
/dev/hda6            2481        2611     1052226   82  Linux swap / Solaris
/dev/hda7            1959        2480     4192902   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19457   156288321    7  HPFS/NTFS

---

### Post by taurus on 2007-06-05
Edit /etc/fstab

```
kdesu kate /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```
And if you want to write to /dev/hdb1, then you need to install ntfs-3g since ntfs driver only lets you read from it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by spookyct on 2007-06-05
that solved it...  and for some reason brought back all the drives...

thanks a lot!

---

