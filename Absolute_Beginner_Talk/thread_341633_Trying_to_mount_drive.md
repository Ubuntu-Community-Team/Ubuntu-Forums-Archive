---
title: "Trying to mount drive"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Deathcab on 2007-01-18
I just installed ububtu and I had a second Harddrive with all my music and stuff on it. I tried to mount it but I got this error. All I really want is my music off this harddrive.

[IMG]http://i14.tinypic.com/4g8nczn.jpg[/IMG]

any tips? I really really want my music](*,)

---

### Post by taurus on 2007-01-18
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Deathcab on 2007-01-18
dennis@dennis-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23947   192354246   83  Linux
/dev/hda2           23948       24321     3004155    5  Extended
/dev/hda5           23948       24321     3004123+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9725    78116031    7  HPFS/NTFS

---

### Post by taurus on 2007-01-18
Open a terminal and edit /etc/fstab.

```
gksudo gedit /etc/fstab
```
Scroll to the end and add this line to it.

```
/dev/hdb1   /media/hdb1   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hdb1
sudo mount -a
df -h
```

---

### Post by Deathcab on 2007-01-19
alright I did all that and Its mounted I belive but its blank and all the folders arnt there. The only thing I want is my music and my pictures. Anyway I can access them?

---

