---
title: "mounting drives (Solved)"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by Donkeyman on 2006-10-11
I'm really struggling here so I hope somone can help

I'm trying to mount a second HDD i have installed on my pc
I ahve created a mount point in the media folder but it won't let me mount the drive there. I've tried to change the permissions of the folder with

chmod 777 /media/linuxdrive

but it says operation not permitted.
I am continaully told I can't change anything on the device because it is owned by root?

Please help me out here. I'm a real newbie to this and all I want to do is mount a drive!

---

### Post by Kateikyoushi on 2006-10-11
Are you using the sudo command ?

Like sudo mount, sudo chmod.

---

### Post by PriceChild on 2006-10-11
Check out this:
[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by Donkeyman on 2006-10-11
> **Kateikyoushi said:**
> Are you using the sudo command ?

Like sudo mount, sudo chmod.

right, i went with sudo chmod and it let me change the permissions (i think) but now when I try to mount it with
sudo mount /dev/hdb /media/linuxstore
it says
mount: you must specify the filesystem type

---

### Post by aysiu on 2006-10-11
Please read the link PriceChild posted.

---

### Post by Donkeyman on 2006-10-11
i think i cracked it, thanks for the help guys

---

### Post by LorenXo on 2006-10-11
Depending on what you're mounting, you probably want to specifify which partition of the device is you want to mount. (If it's partition 1 then you'd use ```
sudo mount /dev/hdb**1** /media/linuxstore
```). If it's failing to autodetect the formatting used on the partition and you know what it is, you can specify it by using [CODE]sudo mount /dev/hdb /media/linuxstore/ -t *FilesystemType*[CODE] (e.g. 'vfat' for fat32, 'ext3' for many linux drives). In gnome, there's a tool called disks-admin that does this for you (in system, administration, somewhere I think).

---

