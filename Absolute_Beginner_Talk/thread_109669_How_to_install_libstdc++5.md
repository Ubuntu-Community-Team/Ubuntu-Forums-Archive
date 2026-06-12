---
title: "How to install libstdc++5???"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by gulfstream2909 on 2005-12-29
I'm a newbie with Ubuntu and am trying to install x-unikey package (a programme that allows me to type Vietnamese in Office softwares).

This is what I've got 

hoanglong@ubuntu:~$ sudo dpkg -i x-unikey-0.92.i386.ubuntu.deb
(Reading database ... 59166 files and directories currently installed.)
Preparing to replace x-unikey 0.92 (using x-unikey-0.92.i386.ubuntu.deb) ...
Unpacking replacement x-unikey ...
dpkg: dependency problems prevent configuration of x-unikey:
 x-unikey depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing x-unikey (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 x-unikey

How can I deal with this???

Many thanks beforehands

---

### Post by Perfect Storm on 2005-12-29
```

sudo apt-get install libstdc++5

```

---

### Post by lutrafobic on 2005-12-29
..and perhaps:

```
sudo apt-get install libstdc++5-dev 
``` 

..too.

---

