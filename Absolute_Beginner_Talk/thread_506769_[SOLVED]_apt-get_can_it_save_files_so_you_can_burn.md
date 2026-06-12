---
title: "[SOLVED] apt-get can it save files so you can burn them to disc"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-07-22
is it possible after you have done an 
sudo apt-get install "program"

that the file you have just d/l you can locate on the hard disc and burn to cdr?

---

### Post by 5-HT on 2007-07-22
Yup, take a look around /var/cache/apt
cheers,

---

### Post by pnix on 2007-07-22
Package files will download to /var/cache/apt/archives.

---

### Post by scxtt on 2007-07-22
**aptitude download <package_name>** -- downloads .deb to current directory ... if you don't want to install it first.

---

### Post by Cappy on 2007-07-22
Also you can check out
AptOnCD:
[http://www.debianadmin.com/create-backup-of-all-packages-using-aptoncd-in-ubuntu.html](http://www.debianadmin.com/create-backup-of-all-packages-using-aptoncd-in-ubuntu.html)

---

### Post by stinger30au on 2007-07-22
awesome thanks for the answers. just what i was looking for

---

