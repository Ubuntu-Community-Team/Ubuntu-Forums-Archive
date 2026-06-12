---
title: "[SOLVED] finding Vista HD"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by frenchsquared on 2007-12-31
ok ubuntu is hd (0,0)
vista is HD(1,0)

how do I make ubuntu see the Vista HD
 on another machine with partition the vista partition shows on desktop

I want Vista HD on this Desktop

---

### Post by scxtt on 2007-12-31
post the output of **sudo fdisk -l**

---

### Post by taurus on 2007-12-31
You have to mount it to /media for it to display an icon on your desktop.  What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by frenchsquared on 2007-12-31
Disk /dev/sda: 160.0 GB, 160000000000 bytes
240 heads, 63 sectors/track, 20667 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20666   156234928+   7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b49cfa3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23786   191061013+  83  Linux
/dev/sdb2           23787       24792     8080695    5  Extended
/dev/sdb5           23787       24792     8080663+  82  Linux swap / Solaris

---

### Post by scxtt on 2007-12-31
sudo mkdir -p /media/sda1
sudo mount /dev/sda1 /media/sda1

there's a bit more involvement if you want to write to an NTFS partition - i've never needed to do that myself, but i'm sure ntfs-3g is up to the task ...

---

### Post by taurus on 2007-12-31
Or edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it so it, /dev/sda1, would be mount automatically each time you boot Ubuntu.

```
/dev/sda1   /media/sda1   ntfs-3g   defaults   0   0
```
Save it and close down gedit window.  Then, install ntfs-3g driver for it.

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sda1
(in case you haven't done so)
```
Just reboot and you should see an icon on your desktop for /dev/sda1.

---

### Post by frenchsquared on 2007-12-31
thanks

---

