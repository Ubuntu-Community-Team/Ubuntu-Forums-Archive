---
title: "ntfs-3g, ntfs-config, fstab, mounting"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by uputer on 2007-09-02
Could anyone who is familiar with:

1) Command line
2) /etc/fstab
3) ntfs-3g
4) ntfs-config
5) read / writing to NTFS partitions

...help me out?   I installed ntfs-3g in Kubuntu (I hope I can receive help here, too) but I ended up modifying my /etc/fstab file.   I am confused now because I am a little more familiar with traditional fstab files although I'm a newbie with the NTFS read/write in Linux and /etc/fstab and mounting in general. 

Anyone want to take a stab at it?   I appreciate any assistance.

---

### Post by jordanmthomas on 2007-09-02
First, I'll need the output of
```
sudo fdisk -l
```
so I can know where your ntfs partition is.
Second, I'll need to know where you want to mount it.

In the case you understand this stuff already, here's the line I use to mount my ntfs partition in /etc/fstab
```
/dev/disk/by-label/external	/media/external	ntfs-3g	users,user,locale=en_US.utf8,force 0 0
```
(you can use /dev/sda1 or something instead of the udev stuff I use)

---

### Post by Genecks on 2007-09-02
mkdir $HOME/Desktop/ntfs-root
ntfs-3g /dev/partition $HOME/Desktop/ntfs-root

/dev/partition = drive partition of your NTFS partition

My lazy, but often more GUI way is to. ....

1. open terminal
- ALT+F2
- xterm
- sudo apt-get install gparted

2. look at the top of the screen near the clock for "System"

System -> Administration -> Gnome Partition editor

view the partitions.
look for the one that is ntfs

you should see something like

/dev/hda1

or else if you have an SATA drive

/dev/sda1

use that as the /dev/partition mentioned above

---

### Post by jordanmthomas on 2007-09-02
> quickest way to do this for a noob would be
easiest, maybe, but certainly not quickest.  ;)

---

### Post by Hospadar on 2007-09-02
do you have ntfs-config installed? if not, ```
sudo apt-get install ntfs-config
sudo ntfs-config
``` this has always auto-setup my ntfs drives just fine with no manual fstab editing.

---

### Post by petoro on 2008-05-11
At last I have found a solution.

My C: NTFS disk had no volume name in Vista. Then it appeared in Ubuntu as something like: 132.2 GB disk.

This strange label "132.2 GB disk", perhaps for the dot in the middle, couldn't be added to the fstab list.

The utility ntfs-config couldn't recognize it either.

So I've loaded Vista, I've renamed the C: volume label from "nothing" to DiskC and then I have been able to configure the fstab properly with ntfs-config in Ubuntu 8.04.


Petoro

---

