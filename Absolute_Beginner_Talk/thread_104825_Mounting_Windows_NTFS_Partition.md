---
title: "Mounting Windows NTFS Partition"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by don'tknowlinux on 2005-12-17
I am trying to mount my windows partition in Ubuntu. I read the section in the Starter Guide, but when i put the commands in the terminal i get:
"sudo: unable to lookup (computer name) via gethostbyname()"
What does this mean, and how do i fix it?

---

### Post by Qrk on 2005-12-17
Looks like your trying to samba into it. If its on your harddrive, you just need to read it. 

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

---

### Post by don'tknowlinux on 2005-12-17
When i put those commands in is when i get the error.

---

### Post by towsonu2003 on 2005-12-17
Looking at [http://ubuntuforums.org/showthread.php?t=104134&highlight=gethostbyname](http://ubuntuforums.org/showthread.php?t=104134&highlight=gethostbyname) ,

please paste the output to the following commands:
```
cat /etc/hosts
cat /etc/hostname
``` Hopefully, from there, someone else will pick up this because I do not know anything about hostnames...

---

