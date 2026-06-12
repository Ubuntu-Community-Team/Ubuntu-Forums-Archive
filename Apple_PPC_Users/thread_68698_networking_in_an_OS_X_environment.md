---
title: "networking in an OS X environment"
date: 2005-09-24
forum: Apple PPC Users
---

### Post by anechoic on 2005-09-24
I have a household with 5 Mac's (laptops and desktops)...we have an iMac G5 acting as the print server for the Mac wireless network...all machines booted into OS X can successfully print over the wireless network and see each other...
(also, I have a Canon i950 which doesn't have any print drivers for Linux but it does for OS X...any info on this?)
but I have not been able to figure out how to get my Ubuntu iBook on the network...
I tried installing [netatalk] last winter but it just hosed my Warty system for some reason and I had to reload everything...
any suggestions, info, tips? 
thanks in advance!
KIM

---

### Post by khc on 2005-09-25
sudo iwconfig eth1 essid NetworkName
sudo dhclient eth1

Assuming that eth1 is your wireless card and NetworkName is your access point name.
Since both OS X and linux uses cups, once you are able get on the network printing should be fine.

---

### Post by anechoic on 2005-09-27
thanks for the info...I tried using iwconfig but I got the following:

kim1@anechoic:~ $ sudo iwconfig eth1 essid anechoicmedia
Password:
kim1@anechoic:~ $ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:30:65:0a:39:12
Sending on   LPF/eth1/00:30:65:0a:39:12
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.100 -- renewal in 245429 seconds.


I'm using a regular Airport card (not extreme) and I have a connection to the router and DSL modem but cannot see any of the other computers OS X and Linux in the house
???

---

### Post by khc on 2005-10-02
What do you mean by "Cannot see"? If you use Network:/// (the nautilus smb browser) if often doesn't work unless you directly specify the IP address of the machine, smbclient on the command line should also work.

---

