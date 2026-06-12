---
title: "apt-get source"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-07-26
f i have done apt-get source mixmaster

then atp-get build-dep mixmaster

lex1@xstation:~$ sudo apt-get source mixmaster
Reading package lists... Done
Building dependency tree... Done
Skipping already downloaded file 'mixmaster_3.0b2-2ubuntu1.dsc'
Skipping already downloaded file 'mixmaster_3.0b2.orig.tar.gz'
Skipping already downloaded file 'mixmaster_3.0b2-2ubuntu1.diff.gz'
Need to get 0B of source archives.
dpkg-source: extracting mixmaster in mixmaster-3.0b2
dpkg-source: unpacking mixmaster_3.0b2.orig.tar.gz
dpkg-source: applying ./mixmaster_3.0b2-2ubuntu1.diff.gz
lex1@xstation:~$ sudo apt-get install build-dep mixmaster
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-dep
lex1@xstation:~$ bulid-dep




then atp-get build-dep mixmaster


does mixmaster still need to be built from source or just configured?





lex1

---

### Post by mlind on 2006-07-26
```

sudo apt-get build-dep mixmaster
apt-get source **-b** mixmaster

```

You can build doing *dpkg-buildpackage -rfakeroot -us -uc* on the source folder (you need fakeroot and dpkg-dev packages for this).

---

