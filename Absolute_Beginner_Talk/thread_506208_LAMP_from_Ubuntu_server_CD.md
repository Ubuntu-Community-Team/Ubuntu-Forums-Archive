---
title: "LAMP from Ubuntu server CD"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-07-21
I am using Ubuntu 7.04 Desktop, i wanted to install LAMP from the Ubuntu server CD.
I mounted the Ubuntu Server CD ISO as /media/iso
and added this entry to sources.list

deb file://media/iso/ fesity main restricted

its packages were shown in synaptic, when i try to install those packages, it tried to get them from internet, how should i use the ISO to avoid installing LAMP online?

---

### Post by p_quarles on 2007-07-21
Here's the line to enable the server CD as a repository ```
deb cdrom:[Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
```
I don't know if that will work for Apache, PHP and MySQL, though. The CD gives you the option of configuring and integrating those elements during the installation, but that doesn't necessarily mean they're available as individual packages. You could try, though.

If that doesn't work --and for whatever reason, you *really* don't want to install these packages from the repos-- you can always use the server CD to reinstall the system, and then install the desktop GUI later. Of course, that would mean using the internet.

---

