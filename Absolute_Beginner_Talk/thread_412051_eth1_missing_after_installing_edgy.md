---
title: "eth1 missing after installing edgy"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by vijayanand_sodadasi on 2007-04-17
Hi,
I am unable to find eth1 in the network settings1.  Earlier in dapper, eth0 and eth1 were active and eth1 was set to default.  Now only eth0 is available.  I am unable to connect to internet because of this I suppose.  I am using dapper live cd to connect to internet.

I did ifup -a but that didn't solve the problem.  The output of that command is :
```
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

```

I also found out that /etc/iftab file had only one entry eth0 in it.  I updated it and added an entry for eth1 and did ifup again, but that didn't help either.

How can I bring back eth1?:confused:

---

### Post by Cypher on 2007-04-17
Check out the boot messages to see if ETH1 was even found during bootup. 
```

dmesg | grep eth

```
Regards

---

### Post by vijayanand_sodadasi on 2007-04-17
```
[17179587.832000] e100: eth0: e100_probe: addr 0xfc500000, irq 201, MAC addr 00:0B:CD:65:4D:30
[17179613.976000] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

eth1 not mentioned anywhere??:confused:

---

### Post by Cypher on 2007-04-17
OK, that means that the hardware wasn't found during the initial probe. Is ETH1 an add-on NIC or is a on-board NIC? Perhaps it has failed?

Regards

---

### Post by handaxe on 2007-04-17
What is ETH1 - a wireless card?  IPW3945? If so, then install the restricted modules for your kernel...

Try ```
sudo lshw -C network
``` to show hardare

HA

---

### Post by vijayanand_sodadasi on 2007-04-18
> **Cypher said:**
> OK, that means that the hardware wasn't found during the initial probe. Is ETH1 an add-on NIC or is a on-board NIC? Perhaps it has failed?

Regards

I think its an onboard NIC card one with USB connection.  I connect the USB port of the ADSL modem into one of the slots available.  I dont think it failed because when I boot with live CD, eth1 is available and the light on ADSL modem is on.  But the problem is only when I boot from harddisk which has Ubuntu 6.10 installed.


Output of lshw -C network
```
network

description:  Ethernet interface 
product:  82801DB PRO/100 VM (LOM) Ethernet Controller 
vendor:  Intel Corporation 
physical id:  8 
bus info:  pci@05:08.0 
logical name:  eth0 
version:  81 
serial:  00:0b:cd:65:4d:30 
size:  10MB/s 
capacity:  100MB/s 
width:  32 bits 
clock:  33MHz 
capabilities:  bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation 
configuration: autonegociation = on 
broadcast = yes 
driver = e100 
driverversion = 3.5.10-k2-NAPI 
duplex = half 
firmware = N/A 
link = no 
multicast = yes 
port = MII 
speed = 10MB/s 
 
resources: iomemory : fc500000-fc500fff 
ioport : 1000-103f 
irq : 201 
 

```

---

### Post by vijayanand_sodadasi on 2007-04-18
Do you think I need to add additional modules and stuff like that or remove some.  Because earlier I had ubuntu 6.06 (Dapper) installed on harddisk and didn't have any problem with that.  Later I did a clean install of ubuntu 6.10 (Edgy) and this happened.

---

### Post by vijayanand_sodadasi on 2007-04-18
Anybody ideas please??

---

### Post by handaxe on 2007-04-18
Are these any help?

[http://ubuntuforums.org/showthread.php?t=395422](http://ubuntuforums.org/showthread.php?t=395422)
[http://ubuntuforums.org/showthread.php?t=126345](http://ubuntuforums.org/showthread.php?t=126345)

Any output from dmesg?
```

Sudo dmesg | grep eth
```

HA

---

### Post by edigs on 2007-04-20
> **vijayanand_sodadasi said:**
> Anybody ideas please??

(New to forums, using different linux distros for few years now, thow. Now using dual-boot Kubuntu & win)

I had similar problem some time ago. Found out that the reason was disabled WiFi under win (using HP  wireless assistant tray icon). After reenabling wifi in windows, eth1 reappered in kubuntu too.

---

### Post by Bachstelze on 2007-04-20
What was eth1 supposed to be, anyway ?

---

