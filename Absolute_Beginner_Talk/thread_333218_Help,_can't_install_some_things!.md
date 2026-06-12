---
title: "Help, can't install some things!"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Stambo00 on 2007-01-07
I'm trying to download a few things but I get this error:

Failed to fetch cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/pool/main/g/glibc/libc6-dev_2.4-1ubuntu12_i386.deb  MD5Sum mismatch

I'm using an edgy CD but it could be a different one from the original I used to install onto my system.

Is there anyway I can download the things I want (namely the linux headers) without the CD?

---

### Post by pay on 2007-01-07
```
sudo nano /etc/apt/sources.list
```and comment out the cdrom (#)

---

### Post by Stambo00 on 2007-01-07
Thankyou! Worked perfectly!

---

