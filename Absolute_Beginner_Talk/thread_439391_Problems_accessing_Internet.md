---
title: "Problems accessing Internet"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by eiolv on 2007-05-10
I cannot access "most" Internet pages. I already got some help at the forum yesterday: [http://ubuntuforums.org/showthread.php?t=437123]("http://ubuntuforums.org/showthread.php?t=437123"). I thought the problem was solved, couse suddenly it seemed to work, but now it's the same thing. Can someone help me?

---

### Post by Najand on 2007-05-10
Try:```
 sudo /etc/init.d/networking restart
```
and try again.

---

### Post by eiolv on 2007-05-10
It makes no difference... I can access gmail, for instance, but most pages won't download.

---

### Post by eiolv on 2007-05-10
This is the output I get if I run the code: 

niklas@stova:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 5127
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

Listening on LPF/eth0/00:14:85:5a:13:08
Sending on   LPF/eth0/00:14:85:5a:13:08
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.80.1 port 67
eth1: ERROR while getting interface flags: No such device 
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device 
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device 
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416 
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0. 
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:14:85:5a:13:08 
Sending on   LPF/eth0/00:14:85:5a:13:08
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.80.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.80.1
bound to 192.168.80.100 -- renewal in 17036 seconds.
                                                                         [ OK ]
niklas@stova:~$

Does this make any sence to anyone?

---

### Post by annda on 2007-05-10
can you repeat the yesterday steps? what helped? maybe some changes were not permanent?

---------

you get an IP so theoretically you should be fine. the only problem that comes to mind is DNS.

check out htis thread:
[http://ubuntuforums.org/showthread.php?t=282034](http://ubuntuforums.org/showthread.php?t=282034)

also for blacklisting IPv6 systemwide:
[http://ubuntuforums.org/showpost.php?p=1553790&postcount=5](http://ubuntuforums.org/showpost.php?p=1553790&postcount=5)

---

### Post by eiolv on 2007-05-10
OK, I did the thing in about:config and the code: sudo ifconfig eth0 mtu 1500, and then it just worked. I will try the things suggested in the threads you gave, annda, it just takes some time, as I can only access the internet in windows, and have to reboot every time I'm trying something in ubuntu.

---

### Post by eiolv on 2007-05-10
Now I tried everything I can think of concerning the DNS, and it still wont work. What's the matter with IPv6? What is it and why is it there if I should just blacklist it?

---

