---
title: "bluez-utils problem"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by pavel_kbc on 2006-11-30
root@r00t-server:/home/r00t# /etc/init.d/bluez-utils restart
bash: /etc/init.d/bluez-utils: No such file or directory
root@r00t-server:/home/r00t# apt-get install bluez-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bluez-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.


please help me . what should i do now ? 

:mad: 

all bluetooth apps installed 

root@r00t-server:/home/r00t# apt-get install gnome-bluetooth obexserver bluez-utils bluez-pin pppconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-bluetooth is already the newest version.
obexserver is already the newest version.
bluez-utils is already the newest version.
bluez-pin is already the newest version.
pppconfig is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
root@r00t-server:/home/r00t#
**root@r00t-server:/home/r00t# /etc/init.d/bluez-utils restart**
**bash: /etc/init.d/bluez-utils: No such file or directory**

](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by pavel_kbc on 2006-12-01
anyone ?

---

### Post by lcohen999 on 2006-12-10
> **pavel_kbc said:**
> anyone ?


/etc/init.d/bluetooth rather than bluez-utils

---

