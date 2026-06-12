---
title: "mysql won't start"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Nutopia on 2008-01-20
Hi! I've followed all of the directions from this post concerning the same issue:
[http://ubuntuforums.org/showthread.php?t=666689](http://ubuntuforums.org/showthread.php?t=666689)

among other forums out there - still can't get this fixed...

If i type: mysql -u root -p -h 127.0.0.1
i can get into mysql 

But when I just try to restart or start the server:
sudo /etc/init.d/mysql restart

the stop succeeds but the start fails. 

If I try to access mysql by just using the mysql command I get:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


in my.cnf, my mind address is set correctly for localhost:
bind-address            = 127.0.0.1
(this was the issue in the post linked above)

Anyone have an idea what to do next? This is preventing php5 from installing properly. 

Help is much appreciated... want to get this new set up ready for work tomorrow. running lamp on windows is slooooooooow!!

---

### Post by Hospadar on 2008-01-20
do you have a mysql server running on your machine?

The client and server programs are different applications, and I believe you have to start the server manually (not to mention install it from synaptic)

---

### Post by Nutopia on 2008-01-20
Ya - it shows its downloaded in the menu. Also, when I run:
sudo /etc/init.d/mysql restart

the server stops but errors out on restart

---

### Post by Nutopia on 2008-01-20
loopback is on too:

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:09:81:73:F5  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe81:73f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78838 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:94897043 (90.5 MB)  TX bytes:5336520 (5.0 MB)
          Base address:0xff00 Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10797 (10.5 KB)  TX bytes:10797 (10.5 KB)

---

