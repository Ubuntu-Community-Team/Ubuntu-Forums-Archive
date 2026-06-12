---
title: "created partition, but don't have permission to access it?"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Bob Walsh on 2006-07-09
create a partition using linex rescue disk while setting up this win server 2003 to duel boot Ubuntu. Duel boots fine, but I don't have permission to write to that partition?

My Unbuntu install is server (to take advantage of 8GB RAM :D ) modified to include Ubuntu desktop (via "sudo apt-get install ubuntu-desktop")

Please help!:confused:

---

### Post by gerbman on 2006-07-10
> **Bob Walsh said:**
> create a partition using linex rescue disk while setting up this win server 2003 to duel boot Ubuntu. Duel boots fine, but I don't have permission to write to that partition?

My Unbuntu install is server (to take advantage of 8GB RAM :D ) modified to include Ubuntu desktop (via "sudo apt-get install ubuntu-desktop")

Please help!:confused:What does your /etc/fstab file look like? You can make yourself the owner of the partition by adding the "uid=username" option, where "username" is your account name.

---

### Post by Bob Walsh on 2006-07-10
OK - there's no uid=bob in fstab. 

But how do I edit it? opened it from the desktop, but it won't let me save changes to it. I suspect I should be working from the command prompt, but I'm a recovering windows programmer!

---

### Post by gerbman on 2006-07-10
> **Bob Walsh said:**
> OK - there's no uid=bob in fstab. 

But how do I edit it? opened it from the desktop, but it won't let me save changes to it. I suspect I should be working from the command prompt, but I'm a recovering windows programmer!Yes, the command prompt isn't that useful in Windows, but it's your best friend in Linux :) Open a terminal with Applications->Accessories->Terminal. Then do```
sudo gedit /etc/fstab
```The line that mounts my second hard drive looks like this:```
/dev/hdb1       /mnt/hd2        vfat    defaults,uid=gerb    0       2
```The fourth column is the option list. Adding uid=bob will make you the owner of the partition when it gets mounted. Hope that helps.

---

### Post by Bob Walsh on 2006-07-10
tried that (thanks), but no luck. Get the follwing message when I try to access it:

Unable to mount the selected volume.
mount: only root can mount /dev/sda6 on /media/sda6 [-X

---

### Post by aysiu on 2006-07-10
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by gerbman on 2006-07-10
> **Bob Walsh said:**
> tried that (thanks), but no luck. Get the follwing message when I try to access it:

Unable to mount the selected volume.
mount: only root can mount /dev/sda6 on /media/sda6 [-XYou'll still need to use "sudo" to mount the partition. Remount the partition with the following:```
sudo umount /media/sda6
sudo mount /media/sda6
```

---

### Post by Bob Walsh on 2006-07-10
umount came back: /media/sda6 not mounted.
mount came back: wrong fs type/ bad option, bad superblock.

I created this partition as part of setting this pc up for duel booting. It is an EXT3. Used quparted from a linux rescue disk. Physical drives are 3 500 GB RAID 5.

Argg!:confused: :confused:

---

### Post by gerbman on 2006-07-11
> umount came back: /media/sda6 not mounted.This means the partition wasn't mounted to begin with. You can look at /etc/mtab to see which partitions are mounted where.> mount came back: wrong fs type/ bad option, bad superblock.My guess is that you have the wrong filesystem type specified in your fstab file. If the partition is EXT3, then the type (third column) of the fstab line should be "ext3". Post your fstab file.> Physical drives are 3 500 GB RAID 5.I have no experience with RAID, which might be causing the problem. Sorry.

---

