---
title: "Manage Partitions"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-10-22
Hello! I was wondering if it is possible to manage partitions after installing Ubuntu? When I installed it on my computer, I made two partitions, but I can only see one listed under "Computer." How do I get the other one? Thanks!

---

### Post by insub2 on 2006-10-22
to manage partitions, the *easiest* way is to install gparted.  it's a got a nice gui.

but i think what you want is to mount your partition.
try this:
```
sudo mkdir /media/name-of-your-choice
sudo mount /dev/hda1 /media/name-of-your-choic/
```

you can name the folder it's mounted to anything you want.
hda1 is the first partition on your harddrive.  your unmounted partition may be hda2.  off the top of my head, use gparted to check this (probably an easier way using the terminal...but i'm no good at the terminal).

---

### Post by CatKiller on 2006-10-22
If one of the partitions that you made was a **swap** partition, then you don't especially wish to see it. It's only useful to the computer. If it was a partition that you do want to use yourself, then mount the partition as insub2 suggests. You may also find these links helpful:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by amitroy5 on 2006-10-22
CatKiller, you are right, I created a swap partition. However, I gave that partition 15 GB. How do I put some of that space to another partition?

---

### Post by CatKiller on 2006-10-22
> **amitroy5 said:**
> CatKiller, you are right, I created a swap partition. However, I gave that partition 15 GB. How do I put some of that space to another partition?

You can either use GParted on the Ubuntu live cd, or GParted on the [GParted live cd]("http://gparted.sourceforge.net/livecd.php") to resize & move your swap partition, and then resize your other partition. You'll probably want to use the command ```
sudo swapoff -a
``` if you use the Ubuntu cd though, since the Ubuntu cd automatically mounts your swap partition for performance reasons when you boot it, and you don't want to be resizing a mounted partition.

Good luck - it's quite straightforward in a point-and-click kind of way.

---

