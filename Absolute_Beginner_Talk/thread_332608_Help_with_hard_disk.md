---
title: "Help with hard disk"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by jglitch on 2007-01-06
Totally new to linux (ubuntu distro). 

Here's my problem. I have installed the latest UBUNTU (6.10) on my Secondary Master. That drive has three partitions. Two of which is an NTFS (surprise, surprise) and an EXT3 file system. During the my installation of UBUNTU, I have created three more partition on my EXT3 to install the root files and the swap files. Now my problem is I can't access the NTFS side of that HDD (hdc)](*,) . Any suggestions?

hda1-Windows XP system
hda(?)-some files

hdc1- "/"
hdc3-"ubuntu files"
hdc4-"/swap"
hdc5-need some help to mount this or access it from ubuntu
hdc6-need some help to mount this or access it from ubuntu

Thanks for you help.

---

### Post by taurus on 2007-01-06
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Scroll down to the end and add these two lines.

```

/dev/hdc5   /media/hdc5   ntfs   nls=utf8,umask=0222   0   0
/dev/hdc6   /media/hdc6   ntfs   nls=utf8,umask=0222   0   0

```
Save it.   Then, create two new mount points and mount them.

```
sudo mkdir /media/hdc5 /media/hdc6
sudo mount -a
df -h
```

---

### Post by jglitch on 2007-01-06
thanks taurus, but it seems, i can't still find those partitions. i have restarted and all.

---

### Post by CroEragon on 2007-01-06
They should be in /media/
Note that it is just read (not write) mounted.
If you want write acces read [this.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")

---

