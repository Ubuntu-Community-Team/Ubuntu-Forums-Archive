---
title: "Unable to mount"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Ix Wraith xI on 2007-03-25
First of all let me say i am a new linux user (of less than a week), i installed Ubuntu 6.06 LTS - The Dapper Drake (32bit pc version) because i am sick of windows.

I can not open my old windows hard drive, i have two hard drives on my computer, the bigger one i installed ubuntu on and the smaller one i used to back up my wallpapers and music to before i installed ubuntu.

A friend said i should post this here:

root@Wraiths-desktop:/home/wraith# sudo fdisk -l

Disk /dev/hda: 30.7 GB, 30738677760 bytes
255 heads, 63 sectors/track, 3737 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3644    29270398+  83  Linux
/dev/hda2            3645        3737      747022+   5  Extended
/dev/hda5            3645        3737      746991   82  Linux swap / Solaris

Disk /dev/hdb: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1025     8233281    c  W95 FAT32 (LBA)
root@Wraiths-desktop:/home/wraith#

Thank you for your help and time.

---

### Post by taurus on 2007-03-25
You need to add an entry in /etc/fstab to mount your fat32/vfat partition.  Open a terminal and type

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Scroll to the end and add this line to it.

```
/dev/hdb1   /media/hdb1   vfat   iocharset=utf8,umask=000   0   0
```
Save the change.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by Bungo Pony on 2007-03-25
sorry, wrong thread

---

