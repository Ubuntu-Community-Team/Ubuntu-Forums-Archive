---
title: "Ubuntu 7.04 net problem"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by alexyi on 2007-08-17
every time i connect to internet, it was time limited,  i have to logon to internet every 6 or 7 minutes, sometimes it works , but sometimes not... i'm beginner, my nerwork configuration was done by administrator at the computer centor of university, the following sencenses were copied from terminal , please help me...

imin@IMIN:~/Desktop$ sudo sh logon.sh
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:16:d4:d8:3b:29
Sending on   LPF/eth0/00:16:d4:d8:3b:29
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPNAK from 129.242.225.209
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 129.242.225.209
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 129.242.225.209
bound to 129.242.225.212 -- renewal in 461 seconds.
imin@IMIN:~/Desktop$

---

### Post by Steve1961 on 2007-08-17
Not sure about this but if you have a look in /etc/dhcp3/dhclient.conf it might say something about the length of lease time

---

### Post by Synflux on 2007-08-17
The NAK is probably because you requested an address that had already been leased to someone else. Then it's sent a discover message, the dhcp server has responded with an offer which has been accepted (the request). Finally the server has accepted your request (the ack) you've ended up with 129.242.225.212. 

The lease time looks very short (approx 8 mins!). As Steve1961 says the dhclient.conf file has an option which is normally commented out:

send dhcp-lease-time xxxx;

where xxxx is the lease time requested (normally 3600). So it would be worth checking although this can be overruled at the server end.

:)

---

### Post by alexyi on 2007-08-18
thank you so much for your advices... i learned a lot... but what exactly should i do? I tried to change that 3600 time limit, but i can't save my changing... it says that i have no authority to change and save....

---

### Post by Steve1961 on 2007-08-18
sudo gedit /etc/dhcp3/dhclient.conf

---

