---
title: "Using a partition with windows &amp; Linux"
date: 2005-06-26
forum: Absolute Beginner Talk
---

### Post by someone447 on 2005-06-26
I am dual booting and I was wondering if I could use a fat32 partition to share between windows and linux, so I can put stuff I download into a shared partition so i can use it from both. in windows I have a c: and an f: drive(the f: is a fat32).  So how would I go about sharing that partition?

---

### Post by sapo on 2005-06-26
[QUOTE=someone447]I am dual booting and I was wondering if I could use a fat32 partition to share between windows and linux, so I can put stuff I download into a shared partition so i can use it from both. in windows I have a c: and an f: drive(the f: is a fat32).  So how would I go about sharing that partition?[/QUOTE]

its easier than you think ;)

sudo mkdir /media/fat32
sudo mount -t vfat /dev/hda3 /media/fat32 -o umask=000

just change you /dev/hda3 for whatever is your windows partition.. if you dont know.. type:

sudo fdisk -l

it will show your partitions ;)

btw take a look here:
[http://ubuntuguide.org/#mountunmountfat](http://ubuntuguide.org/#mountunmountfat)

---

### Post by someone447 on 2005-06-26
> **sapo]its easier than you think  said:**
> http://ubuntuguide.org/#mountunmountfat[/url]
 thanks, that helped alot I got it now, I think i am finally starting to understand linux

---

### Post by poofyhairguy on 2005-06-26
[QUOTE=someone447]thanks, that helped alot I got it now, I think i am finally starting to understand linux[/QUOTE]


Good. Thats when it gets fun.

---

