---
title: "no DHCP on iMac"
date: 2008-09-05
forum: Apple Hardware Users
---

### Post by applefat on 2008-09-05
Hi, Ubuntu 6.04 is installed on an old iMac G3 (the type where the whole device is built into the monitor). I reinstalled it brand-new, out of the box as of yesterday.

I originally had this at home, and then I brought it to the dormitories with me when school started. At home, connecting required no Ubuntu configuration (that I remember). I just plugged the ethernet cable into the home router (Belkan), and open my browser after boot. This is the same for OS X 10.2, which is installed on a second partition.

But now at the dorms, no matter what I do I cannot connect to the network! The situation is such that in my room there is just a rj-45 jack in the wall which I plug the computer directly into. If I plug my WinXP laptop in, bam internet in 20 seconds. NOTHING on this iMac. I can't even assign a static address as far as I can tell... and anyway how am I supposed to know what address to give it? There are at least a hundred folks on this network. I copied the DHCP stuff that I see via ipconfig /all on the XP machine, and cannot ping any of those machines (host unreachable).

ifconfig gives me this:
```
amills@pumpkin:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:65:DE:3B:D2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:41 Base address:0x7000 

eth0:avah Link encap:Ethernet  HWaddr 00:30:65:DE:3B:D2  
          inet addr:169.254.8.155  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:41 Base address:0x7000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:310 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0 
          RX bytes:26966 (26.3 KiB)  TX bytes:26966 (26.3 KiB)

amills@pumpkin:~$ 
```

You'd think it'd be a hardware issue. But, it worked before, and apparently loopback is working (assuming that requires an operational network card). That avah address seems bogus,not even close to the ip adresses I've looked at, there's not much I can do with it. Any ideas...?

---

### Post by prshah on 2008-09-05
> **applefat said:**
> 
 If I plug my WinXP laptop in, bam internet in 20 seconds. NOTHING on this iMac.

Plug it in, open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo /etc/init.d/networking restart
```

Wait for it to complete, and then try the Internet again. If it doesn't work, give the following commands and post the output here```

sudo mii-tool eth0
sudo dhclient eth0
```

btw, I've used ubuntu from 6.10 onwards only, so I don't know if these commands will be available on your system (ubuntu 6.04). Won't create any harm though.

You can ignore the avahi interface; it's designed to "publish" selected network features from your machine.

---

### Post by applefat on 2008-09-05
You can see, that restarting doesn't seem to do much (eth0 is my only NIC). But, I've been thinking, maybe the DHCP server simply doesn't play well with Ubuntu, or at least this version (7.04, sorry, I mistyped). I'm downloading 7.10 right now, maybe that will help? Or perhaps you have some other suggestion?


```
**amills@pumpkin:~$ sudo /etc/init.d/networking restart**
Password:
Sorry, try again.
Password:
 * Reconfiguring network interfaces...                                       RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 7504
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:30:65:de:3b:d2
Sending on   LPF/eth0/00:30:65:de:3b:d2
Sending on   Socket/fallback
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 269096456
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 269096456
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 269096456
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file /var/run/dhclient.eth0.pid with pid 269096456
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:30:65:de:3b:d2
Sending on   LPF/eth0/00:30:65:de:3b:d2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                      [ OK ]
**amills@pumpkin:~$ sudo mii-tool eth0**
eth0: no link
**amills@pumpkin:~$ sudo dhclient eth0**
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:30:65:de:3b:d2
Sending on   LPF/eth0/00:30:65:de:3b:d2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
amills@pumpkin:~$ 
```

---

### Post by jbrown96 on 2008-09-05
Prshah suggested everything that I would try to get it working. Do you still have OS X? That might be worth a try. Maybe there is a problem with the hardware after the move. Are the status lights on the iMac's network port blinking? You might also try to find someone with a router, and see if you can get an ip address with that.

---

### Post by prshah on 2008-09-05
> **applefat said:**
> 
 maybe the DHCP server simply doesn't play well with Ubuntu, 

```
**amills@pumpkin:~$ sudo /etc/init.d/networking restart**
 * Reconfiguring network interfaces...                                       [color=red]RTNETLINK answers: No such process[/color]
There is already a pid file /var/run/dhclient.eth0.pid with pid 7504
eth1: ERROR while getting interface flags: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
Failed to bring up ath0.
**amills@pumpkin:~$ sudo mii-tool eth0**
[color=red]eth0: no link[/color]

```

I don't believe this to be a DHCP server issue at all. Clearly your ubuntu system has been grossly mis-configured, which is probably why mii-tool thinks that no wire is plugged into the system.

Considering that you have only one ethernet connection (and a wireless network card). the other eth2,3 are possibly aliases of ath0 (Atheros wireless card).

In any case, upgrading to 7.10 should clear up the problems (replace configuration files when asked). Remember that you need the alternate CD for upgrading the system; with the live CD, you will have to delete everything and start from scratch.

If for any reason you don't want to upgrade, post the outputs to the following command to start troubleshooting```
cat /etc/network/interfaces
```

---

