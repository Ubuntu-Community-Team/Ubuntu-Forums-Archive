---
title: "Lotta Files Want to transfer from Windows XP to Ubuntu"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by JBernal on 2005-12-11
Hello everyone.  I am very new to Linux and Ubuntu.  I have a lot of files (Music, movies, and Pixs) that i want to transfer over to ubuntu from windows xp.  I have WXP on a 20gb drive and just got a new 160gb drive added on yesterday.  is there such a way or a program to transfer files such as thoes??  

And also, I had some problmes viewing movies that are online,  both in windows media player and quicktime on ubuntu that i didnt have with WXP  is there a way to view these movies on what is provided or is there another program that i can download.  

Thank you in advance for your help.

---

### Post by dcast on 2005-12-11
try going into the disks utility and making the drive accessible -->administration-->disks i think im doing a reinstall as we speak. You will need to download the proper codecs/plugins to view those movies

---

### Post by aysiu on 2005-12-11
Is Ubuntu already installed on the 160 GB drive?

---

### Post by JBernal on 2005-12-11
[QUOTE=aysiu]Is Ubuntu already installed on the 160 GB drive?[/QUOTE]
Yes it is.  on a 40gb partition.  my WXP is on the original 20gb hard drive.

---

### Post by aysiu on 2005-12-11
Can you post the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by JBernal on 2005-12-22
[QUOTE=aysiu]Can you post the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```[/QUOTE]

```
 Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           4       32098+  de  Dell Utility
/dev/hda2   *           5        2433    19510942+   7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *       14595       19411    38692552+  83  Linux
/dev/hdb2               1        7295    58597056    b  W95 FAT32
/dev/hdb3            7296       14594    58629217+   b  W95 FAT32
/dev/hdb4           19412       19457      369495    5  Extended
/dev/hdb5           19412       19457      369463+  82  Linux swap / Solaris

Partition table entries are not in disk order
jbernal@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb1              37G  2.0G   33G   6% /
tmpfs                  62M     0   62M   0% /dev/shm
tmpfs                  62M   13M   50M  20% /lib/modules/2.6.12-10-386/volatile
```[/QUOTE]

---

### Post by aysiu on 2005-12-22
```
sudo mkdir /windows
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Add in this line ```
/dev/hda2  /windows  ntfs  nls=utf8,umask=0222  0  0
``` Save (Control-X), confirm (y), and exit (Enter). Then ```
sudo mount -a
```

---

