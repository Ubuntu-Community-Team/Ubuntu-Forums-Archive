---
title: "2 drives"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Sanus Compleo on 2007-02-14
Okay, I don't know if it has been asked before, but it probably has... I have two hard drives, my master has ubuntu, and 13 gigs on it, and the other, my slave, has xp, and 81 gigs on it, I would like to know how to get my ubuntu hard drive to recognize my other drive, so I can store stuff on it.  Is that even possible?

going to work on gimp and w8t for answer.

---

### Post by taurus on 2007-02-14
If you want to write to ntfs from Ubuntu, then you need to use ntfs-3g.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by pay on 2007-02-14
What format is the partition on the XP drive?

---

### Post by Jussi01 on 2007-02-14
Theres a nice script for setting it up in fstab so it loads every time: 


[http://ca.geocities.com/ic56@rogers....ter-latest.txt](http://ca.geocities.com/ic56@rogers....ter-latest.txt)

---

### Post by taurus on 2007-02-14
> **Jussi01 said:**
> Theres a nice script for setting it up in fstab so it loads every time: 


[http://ca.geocities.com/ic56@rogers....ter-latest.txt](http://ca.geocities.com/ic56@rogers....ter-latest.txt)

You need to fix your link.

---

### Post by Jussi01 on 2007-02-14
> **taurus said:**
> You need to fix your link.

Doh, well heres the google cache...

[Google cache](http://64.233.167.104/search?q=cache:zzYaJlTxioYJ:ca.geocities.com/ic56%40rogers.com/65/diskmounter-latest.txt+http://ca.geocities.com/ic56%40rogers.com/65/diskmounter-latest.txt&hl=en&ct=clnk&cd=1&gl=us)

---

### Post by Sanus Compleo on 2007-02-14
Well, actually there is no partition, it is xp pro, so it cannot be partitioned, and the 13 gig i have has no other os, just ubuntu... I might put another linux on it too...

---

### Post by Sanus Compleo on 2007-02-14
I am sorry for double posting, but I need help, I can't run on 13 gigs, with only 6 free... please help me access my other hard drive!

---

### Post by tommcd on 2007-02-14
Do you see the windows drive listed when you do <cat /etc/fstab> in terminal? If so you should be able to mount it. You can do <mkdir /media/windows> to create a directory for it. Then you should be able to mount it with the mount command. If your windows drive is not there it can be added. Post your fstab. Also post <sudo fdisk -l>
Also, see this:
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28mount%29%7C%28windows%29](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28mount%29%7C%28windows%29)
and this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Sanus Compleo on 2007-02-14
Disk /dev/hda: 13.0 GB, 13020069888 bytes
255 heads, 63 sectors/track, 1582 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1514    12161173+  83  Linux
/dev/hda2            1515        1582      546210    5  Extended
/dev/hda5            1515        1582      546178+  82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9963    80027766    7  HPFS/NTFS


that is my f thingy...

---

### Post by taurus on 2007-02-14
Edit /etc/fstab

```
gksudo gedit /etc/fstab
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

---

### Post by Sanus Compleo on 2007-02-14
Omg
I Got It To Work!!!
This Is Resolved, Yaaaaaaaaaaaaaaaaaaaaaaaaaaaay!!!!!!!!!!!!!!!!!!!!!!!!1

---

### Post by tommcd on 2007-02-16
That looks like your <fdisk -l>. Windows is your 2nd hard disk, listed as:
/dev/hdb1 * 1 9963 80027766 7 HPFS/NTFS
at the bottom. Just follow the 2nd link I gave you:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
1) sudo mkdir /windows (makes a directory for windows)
2)sudo cp /etc/fstab /etc/fstab_backup (backs up your fstab, where all your mount points are)
3)see if the windows drive is listed when you do <cat /etc/fstab> You will know it's windows beacuase the file system in NTFS.
4)edit the fstab according to the psychocats link. Dont worry about the UUID stuff. You really don't need it. Your windows drive will be /dev/hdb1 instead of /dev/hda1 in the psychocats linked page. The rest of the line should be the same. Instead of nano you can use <gksudo gedit /etc/fstab> to edit the file.

---

