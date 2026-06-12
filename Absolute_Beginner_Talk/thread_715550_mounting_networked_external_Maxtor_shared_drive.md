---
title: "mounting networked external Maxtor shared drive"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by blubyu1914 on 2008-03-05
Hello All..

I have searched this forum, but can't seem to find the exact answers I'm looking for. I have an desktop running Ubuntu 7.10 and would like to access my Maxtor external network drive.. I really don't know where to start. I have two other laptops running Windows XP and can access this drive by the installation software provided. Maxtor does not have anything via there website to support Linux.  So far, I've run command- fdisk. Here are my results:
Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)

Not sure what this means to me???  Any help would be greatly appreciated.

---

### Post by spiderbatdad on 2008-03-05
```
sudo fdisk -l
df -h
```

---

### Post by blubyu1914 on 2008-03-05
here's my command response for both codes:

Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

  Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4658    37415353+  83  Linux
/dev/hda2            4659        4863     1646662+   5  Extended
/dev/hda5            4659        4863     1646631   82  Linux swap / Solaris


Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  8.4G   25G  26% /
varrun               1007M  212K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M   80K 1007M   1% /dev
devshm               1007M     0 1007M   0% /dev/shm
lrm                  1007M   23M  985M   3% /lib/modules/2.6.22-14-generic/volatile


Any ideas??

---

### Post by spiderbatdad on 2008-03-05
I think I finally caught on to what you're talking about, at least partly. At first I assumed the drive was attached to your system. It is actually a "network place" routable I presume. I have no idea how to set that up...include it in /etc/network/interfaces if you can discover it with nmap? Maybe contact maxtor for support (ack doubtful) Good luck. Hope you get it...if so, please keep us posted.

---

### Post by blubyu1914 on 2008-03-05
yes, you are correct. It is a "networked" storage drive. Sorry, I'll try to be more specific in my explanation next time.. The Maxtor website doesn't offer any support for Linux based systems at this time. I have the room to add additional internal drives.. Looks like that will be my solution.

best regards,

---

