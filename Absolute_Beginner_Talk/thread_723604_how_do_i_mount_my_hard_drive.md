---
title: "how do i mount my hard drive?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Uberpaws on 2008-03-13
I am completely new to linux.  I have been reading posts on mounting hard drives, but none of them seemed to work.  One told me to make a directory and mount it from there, but the terminal keeps giving me errors.

uberpaws@alpha:~$ fdisk -l

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50afad70

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384512    7  HPFS/NTFS

uberpaws@alpha:~$ sudo mkdir /mnt/sdb1
uberpaws@alpha:~$ sudo mount -a
uberpaws@alpha:~$ 

After doing this, I go to places - computer - hard drive and is still can not mount it.
what should i do?
:confused::confused::confused::confused::confused:

---

### Post by {BzF}~JOKesTER on 2008-03-13
If The Harddrive Shows Up In "Computer" Folder In Ubuntu Than Double Click It.

Post The Output Here Please:

---

### Post by Daveth on 2008-03-13
this should help you along. Do make a backup copy of the /etc/fstab file though, in case things go wrong!!

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by taurus on 2008-03-13
```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media/sdb1
```

---

### Post by Rocket2DMn on 2008-03-13
Can you post the output of
```
cat /etc/fstab
```
If the drive in question is not listed there and is an internal drive, you will need to add it appropriately.  Show us and we can help you do that.
Or is this drive external that you plug in periodically?

---

