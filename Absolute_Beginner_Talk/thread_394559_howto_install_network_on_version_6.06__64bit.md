---
title: "howto install network on version 6.06 / 64bit"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by koukkis on 2007-03-27
hello

I have a HP XW4400 and ubuntu-6.06.1-desktop-amd64.iso installed, but no network!

ok
then I downloaded from Intel e1000.7.4.35 and unzipped in /usr/local/src as explainded.
(sorry, copied the files with USB stick)

Install.txt says do a MAKE INSTALL, but there is no make in ubuntu!

how do I install network driver?

rgds Anders

---

### Post by koukkis on 2007-03-27
old title "howto install network on version 6.06 / 64bit"

when trying to install make from cdrom i get th error message;

W: failed to fetch cdrom [Ubuntu 6.06.1_Dapper drake_-Release amd64 (20060806.1)]/pool/main/m/make/make_3.80+3.81.b4-1_amd64.deb
MD5SUM mismatch

where am i doing wrong?

rgds Anders

---

### Post by zvacet on 2007-03-27
```
gksudo gedit etc/apt/sources.list
```
In fron of line cdrom put # sign
save and close
```
sudo aptitude install make
```

---

### Post by lamalex on 2007-03-27
```
apt-get install build-essential
``` will get you all of the build tools you need.

---

