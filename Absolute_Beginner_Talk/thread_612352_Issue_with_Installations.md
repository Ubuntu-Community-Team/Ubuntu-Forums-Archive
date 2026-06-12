---
title: "Issue with Installations"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Pyrophelia on 2007-11-13
```
E: /var/cache/apt/archives/kdelibs4c2a_4%3a3.5.8-0ubuntu3.1_i386.deb: files list file for package `kdelibs4c2a' is missing final newline
```

Ignore the first part, the package kdelibs4c2a seems to be corrupt. Anyone know a way to fix this?

---

### Post by Partyboi2 on 2007-11-20
> **Pyrophelia said:**
> ```
E: /var/cache/apt/archives/kdelibs4c2a_4%3a3.5.8-0ubuntu3.1_i386.deb: files list file for package `kdelibs4c2a' is missing final newline
```Ignore the first part, the package kdelibs4c2a seems to be corrupt. Anyone know a way to fix this?

Have you tried:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get remove kdelibs4c2a

```Another possible way is to move the corrupt package.
See here: 
[https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html)
or
look in /var/lib/dpkg/info/ for kdelibs4c2a and delete  the file
then 
```
sudo apt-get remove kdelibs4c2a --purge
sudo apt-get install kdelibs4c2a
```Apt-get will spit out some warnings about missing files but should uninstall the file then reinstall.
Hope this helps
:):)

---

