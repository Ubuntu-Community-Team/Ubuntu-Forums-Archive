---
title: "Upgrading to 7.04 problems"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-04-06
ok i upgraded to 7.04 from 6.10 and have had something go wrong. when I turn my PC on I get to the screen where it tries to load gnome. But all i see is the loading cursor rotating. It has ben sitting like that for a good time now. How could I fix this?

---

### Post by zvacet on 2007-04-06
Try with ctrl+alt+F1
```
sudo /etc/init.d/gdm start
```

---

### Post by Aircooledmadness on 2007-04-06
Also,  sometimes the new packages that the devs push out have bugs in them.  They usually catch them a few hours or days later.  

If I have a problem with Feisty,  I usually log in in Single User Mode (you can select this from grub right when your computer starts) and then log in.  Once logged in, run a apt-get update && apt-get upgrade.  Usually that pulls down some new packages and fixes the problem.

---

### Post by ProjectWhat on 2007-04-08
ok that doesnt work. Either of them. Thesame thing happens. But I do get an error when go to ctrl+alt+F1. It says:
```

Starting up...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/343fff66-68e8-4989-b9c4-dc836a72b120) = sda5(8,5)
Kinit: trying to resume from /dev/disk/by-uuid/343fff66-68e8-4989-b9c4-dc836a72b120
Kinit: No resume image, doing normal boot...

Ubuntu feisty (development branch) ben-ubuntu tty1

ben-ubuntu login: _

```

---

### Post by zvacet on 2007-04-09
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

