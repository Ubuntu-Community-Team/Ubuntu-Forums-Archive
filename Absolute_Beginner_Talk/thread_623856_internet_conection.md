---
title: "internet conection"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by Willye on 2007-11-26
hi friends, i have installed ubuntu server 7.10 but i have 2 problems
1. i want to use gnome, how to install this environment and all others features that come with desktop version 
2. when i tried to update my system with: sudo aptitude update, linux tried to connect to internet but it couldn't, i have a huawei smartax ADSL modem and it works perfectly in xp
what happend ?

---

### Post by Willye on 2007-11-26
i have rebooted linux several times and i have powered off my modem too

---

### Post by skymera on 2007-11-26
type ifconfig too see your device name, eth0 wlan0 for example

then

sudo ifup <device name>

im not sure havwe a go at them

---

### Post by Willye on 2007-11-26
whein i run ifconfig appears:
eth0 configured well and 
lo configured well

---

### Post by Willye on 2007-11-26
and ??????????

---

### Post by maybeway36 on 2007-11-26
2. ```
sudo aptitude install ubuntu-desktop
```

---

### Post by calemus on 2008-02-26
i ran the first ting told to run, box disapears and nothing seemed to happen, i typed the thing the next person told to type, nothing seemed to happen, i am runnig kubuntu 7.1, and i cant even find enough of the program for it to tell me my pc stats, processor ram or even the etherernet i am not getting conection from.      >simmer<
need internet connection. pleas help.

---

