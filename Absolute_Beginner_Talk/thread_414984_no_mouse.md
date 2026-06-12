---
title: "no mouse"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Art_Redwood on 2007-04-20
I have just upgrade to ubuntu 7.04, it is running inside virtual pc 07, everything went fine, until I completed the upgrade, and the virtual machine rebooted, ubutnu recognizes my wireless key board, (I can log in) but it does not recognize my cordless mouse, there fore, I can not use it, I have both an acer cordless key broad and mouse, both have the acer brand, but they are both manufactured by logitech, any suggestions I have also tried an old fashion mouse, by plugging it into the back of the computer, and rebooting, still nothing, any suggestion would be welcome

Thanks in advance...

---

### Post by rxtx on 2007-04-20
Have you tried re-running Xconfig?

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Loki-uk on 2007-04-20
This would appear to be a Feisty issue in general and not a VPC issue. We'll need to be patient whilst they sort it out.

Brian

---

### Post by nommo on 2007-04-23
Yup - I just upgraded a virtual install of Xubuntu and have the same issue wih the mouse...

Bugtrack:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87262]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87262")

---

### Post by 3rdgear on 2007-04-23
I re-installed 3 different times to try to remedy the mouse situation, and NONE of them worked. I am back using EDGY.......

---

