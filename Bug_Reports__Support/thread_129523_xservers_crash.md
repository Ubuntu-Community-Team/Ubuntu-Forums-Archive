---
title: "xservers crash"
date: 2006-02-13
forum: Bug Reports / Support
---

### Post by dilitimor on 2006-02-13
dear all
is there any way to reconfigure xserver / xwindows without reinstalling ubuntu
i am using old laptop and did not know its hardware configuration.

today i am going to back all data and reinstall ubuntu

dili

---

### Post by encompass on 2006-02-13
sure... at a console type
```
sudo dpkg-reconfigure xserver-xorg
```
and when your done type...```
sudo killall gdm
```
then type ```
sudo gdm
```
Is this what you needed?

---

### Post by heimo on 2006-02-13
[quote=dilitimor]dear all
is there any way to reconfigure xserver / xwindows without reinstalling ubuntu
i am using old laptop and did not know its hardware configuration.

today i am going to back all data and reinstall ubuntu

dili[/quote]
Wrong forum. [-(

---

