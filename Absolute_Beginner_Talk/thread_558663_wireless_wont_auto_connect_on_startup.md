---
title: "wireless wont auto connect on startup"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-09-24
the only way I can seem to connect to my wireless is with the Wireless Assistant (I use KDE), heres my /etc/network/interfaces

```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface ra0 inet dhcp
wireless-essid aston
wireless-key A4F2A24E4xxxxxhiddenxxxxxx
wireless-channel 11
auto ra0


```

the wireless key is correct (WEP 128) and the essid is correct.
when I run /etc/init.d/networking restart i get the following:

```

pete@pete-laptop:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.ra0.pid with pid 5294
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:13:d3:6d:97:77
Sending on   LPF/ra0/00:13:d3:6d:97:77
Sending on   Socket/fallback
DHCPRELEASE on ra0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.ra0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/00:13:d3:6d:97:77
Sending on   LPF/ra0/00:13:d3:6d:97:77
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]

```


ideas?!

---

### Post by bone2006 on 2007-09-24
are you using ndiswrapper?

---

### Post by Austin_KW on 2007-09-24
Is that a ralink chipset?
change the interfaces ra0 entry to
```

iface ra0 inet dhcp
auto ra0
        pre-up ifconfig ra0 up
	pre-up iwconfig ra0 essid aston
	pre-up iwconfig ra0 key A4F2A24E4xxxxxhiddenxxxxxx 

```

---

