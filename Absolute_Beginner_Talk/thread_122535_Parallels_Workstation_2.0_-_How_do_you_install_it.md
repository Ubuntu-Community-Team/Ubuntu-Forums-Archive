---
title: "Parallels Workstation 2.0 - How do you install it?"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by JAwuku on 2006-01-27
Hello everyone,

I was just wondering how do you install Parallels Workstation 2.0 in Ubuntu? Has anybody managed successfully to install it? If so, could they please elaborate on how it was done? Thanks

---

### Post by JAwuku on 2006-01-29
i read the Parallels FAQ,[ http://www.parallels.com/en/support/faq/]("http://www.parallels.com/en/support/faq/") and loaded the linux-headers for my kernel (K7). Also, not detailed in the FAQ, was the need to install gcc-3.4. Once installed, it compiled cleanly, and I am now free to run virtual machines!

---

### Post by Alexander Grundner on 2006-05-20
[QUOTE=JAwuku]Hello everyone,

I was just wondering how do you install Parallels Workstation 2.0 in Ubuntu? Has anybody managed successfully to install it? If so, could they please elaborate on how it was done? Thanks[/QUOTE]

[Parallels requires the following packages before installing on Ubuntu](http://www.parallels.com/en/support/fullfaq/#answer18):

```
apt-get install linux-headers-`uname -r`
apt-get install gcc
apt-get install libc6-dev
apt-get install make
apt-get install gcc-3.4
apt-get install libstdc++5
apt-get install libqt3-mt
```

I went through the process and Parallels installed smoothly :)

---

