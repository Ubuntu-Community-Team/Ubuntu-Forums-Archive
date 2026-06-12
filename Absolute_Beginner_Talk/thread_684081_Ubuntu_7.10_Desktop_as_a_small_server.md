---
title: "Ubuntu 7.10 Desktop as a small server???"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Jim2029 on 2008-01-31
Is it possible to host about 3 websites, ftp for updating the sites, and an e-mail server for about 60 people on ubuntu 7.10 desktop edition? I'd really like a GUI cause I'm still new to linux. I know how to do all of this in windows... but I linux cause of the cost and the lack of virus. if it is possible, can anyone point me to a how-to page or something?

Thanks.

---

### Post by OffAxis on 2008-01-31
try ispconfig
[http://www.ispconfig.org/]("http://www.ispconfig.org/")

---

### Post by aeiah on 2008-01-31
ubuntu server is the same as ubuntu but without a desktop environment as far as i know, so yea. as for whether it can handle the loads, that all depends on the power of the hardware. it should probably be alright.

although the server cant get any viruses, be aware that as an email server, it will not protect the users from getting email with viruses in. you will need extra protection (in the form of antivirus software on the server, or on the users's computers as normal).

---

### Post by PinkFloyd102489 on 2008-01-31
Most email installations include ClamAV and SpamAssassin in the directions.

---

### Post by brennydoogles on 2008-01-31
> **aeiah said:**
> ubuntu server is the same as ubuntu but without a desktop environment as far as i know, so yea. as for whether it can handle the loads, that all depends on the power of the hardware. it should probably be alright.

although the server cant get any viruses, be aware that as an email server, it will not protect the users from getting email with viruses in. you will need extra protection (in the form of antivirus software on the server, or on the users's computers as normal).

I recommend installing from the ubuntu server edition cd ( which will set up all of the server needs you have), and afterwards installing a desktop environment like this:

Ubuntu (Gnome... Standard Ubuntu look)```
sudo aptitude install ubuntu-desktop
```
Xubuntu (XFCE, lighter on resources... and my recommendation to you )```
sudo aptitude install xubuntu-desktop
```
Kubuntu (KDE... looks more like windows and is very popular)```
sudo aptitude install uubuntu-desktop
```
I hope this helps, and good luck!!

---

