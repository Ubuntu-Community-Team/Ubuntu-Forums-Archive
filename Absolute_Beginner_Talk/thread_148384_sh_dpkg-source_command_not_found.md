---
title: "sh: dpkg-source: command not found"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by awalesminfo on 2006-03-22
hi guys am new to kubuntu and facing following problem when i download any source , i got the tar file of source in my home folder but still i want to know why this is happening ??:-k 

---@--- :~$ sudo apt-get source qt3-dev-tools
Reading package lists... Done
Building dependency tree... Done
Need to get 17.5MB of source archives.
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/main qt-x11-free 3:3.3.4-8ubuntu5 (dsc) [1787B]
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/main qt-x11-free 3:3.3.4-8ubuntu5 (tar) [17.4MB]
29% [2 qt-x11-free 5082166/17.4MB 29%]                                                                                                      6283B/s 32m56s^Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/main qt-x11-free 3:3.3.4-8ubuntu5 (diff) [76.6kB]
Fetched 17.5MB in 32m8s (9076B/s)
sh: dpkg-source: command not found
Unpack command 'dpkg-source -x qt-x11-free_3.3.4-8ubuntu5.dsc' failed.
E: Child process failed

---

### Post by jrib on 2006-03-22
Install the build-essential package, it will pull in dpkg-dev.  If you plan on compiling you should just go for build-essential though

---

