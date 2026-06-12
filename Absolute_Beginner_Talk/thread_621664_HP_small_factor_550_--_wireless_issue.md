---
title: "HP small factor 550 -- wireless issue"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by ibm450 on 2007-11-23
hi guys, im absolutly a newbee to linux, been a xp user for many years now, and today i bought APC mag that had Ubuntu live CD ISO.

the live cd works a treat on my HP compaq small factor, in likes of performance and was suprised how responsive it was running on the cd live ;)

i have ActionTec 802.11b usb wi adapter and cannot seem to config it. i can see it showing wlan0 but thats as far as it goes. ive tried the sudo things in terminal but cannot get the sudo ifconfig wlan0 up to work, i get SIOCSIFFLAGS: NO SUCH DEVICE

i\so i assume that the adapter isnt reconised by ubuntu?:confused:

ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5782 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: eth0
       version: 03
       serial: 00:0e:7f:64:b9:94
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 firmware=5782-v3.13 latency=64 mingnt=64 module=tg3 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: wlan0
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
ubuntu@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

ubuntu@ubuntu:~$ sudo ifconfig wlan0 down
ubuntu@ubuntu:~$ sudo dhclient -r wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:00:00:00:00:00
Sending on   LPF/wlan0/00:00:00:00:00:00
Sending on   Socket/fallback
ubuntu@ubuntu:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such device
ubuntu@ubuntu:~$ 


any1 can help:(

---

