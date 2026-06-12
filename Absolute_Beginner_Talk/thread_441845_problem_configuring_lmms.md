---
title: "problem configuring lmms"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-05-13
I downloaded the i386 gzip file from their website, extracted it, but when I go to configure I get this.

checking QTDIR... configure: error: *** QTDIR must be defined, or --with-qtdir option given

I put on the option after creating a folder.

 ed@ed-desktop:~/source_files/lmms-0.2.1$ ./configure -with-qtdir=/home/ed/lmms

What gives? I cant seem to define it ever...

---

### Post by seshomaru samma on 2007-05-13
lmms is in the repos
why don't you just go
```
sudo aptitude install lmms
```

---

