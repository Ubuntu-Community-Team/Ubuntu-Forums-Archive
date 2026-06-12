---
title: "libstdc++-libc6.2-2.so.3 missing on amd64 System"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by lwh on 2006-09-27
Hi

Im setting up an Xeon EMT64 (64bit) server, and is installing an Intel webinterface for the raid controller (Intel RAID Web Console), but the webinterface which is running jave needs  libstdc++-libc6.2-2.so.3  :-(  which is missing.

Do any one know a way to get the libstdc++-libc6.2-2.so.3 installated on a amd64 bit system ?

Running Ubuntu 6.06 (very new into the world ubuntu, but know my way arround in debian)
/LWH

---

### Post by lwh on 2007-07-06
Sloved the issue by downloading  libstdc++2.10-glibc2.2_2.95.4-24_i386.deb and force the install using dpkg -i -forcearchtecture 

Next up was getting the the intel raid web console up running, which was a bit tricky, since the readme from intel has some errors.
but basicly 
to start the regserver run /usr/sbin/RegSvr
Next Start RSLinux by running /usr/sbin/RSLinux
Finally start the intel webservice by running sh /opt/SVR/startup.sh

now it's possible to connect to port 3570 in the server and manage the Inten Raid Controller.
SWEET AS

---

