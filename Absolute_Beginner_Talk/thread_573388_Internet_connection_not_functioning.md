---
title: "Internet connection not functioning"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by thebrandon on 2007-10-11
I just install Ubuntu recently on one of my computers but I cant seem to get either the onboard Lan or the ethernet card to connect.  Both are detected and, from what I have read, are using the appropriate drivers.  When I plug the cable in the system tries to get a connection and then says its connected after about 45 seconds or so but I still get Server Not Found error in firefox.

I am using Ubuntu 7.04 and trying to connect with either a Marvell 88E8001 (Onboard LAN [asus a8v deluxe]) or a Realtek RTL-8139 pci card both which give the same result.

I have tried turning the onboard lan on and off in the bios as well as updating the bios to the latest version.

I also tried to run a liveCD version of both Ubuntu and OpenSuse to see if either would give me an internet connection and neither did.

ifconfig :

eth0      Link encap:Ethernet  HWaddr 00:11:2F:DE:4A:98  
          inet6 addr: fe80::211:2fff:fede:4a98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:561628 (548.4 KiB)  TX bytes:12642 (12.3 KiB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:00:C5:C1:E9:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x6000 

eth0:avah Link encap:Ethernet  HWaddr 00:11:2F:DE:4A:98  
          inet addr:169.254.7.42  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

eth1:avah Link encap:Ethernet  HWaddr 00:00:C5:C1:E9:62  
          inet addr:169.254.9.92  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:862 errors:0 dropped:0 overruns:0 frame:0
          TX packets:862 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68508 (66.9 KiB)  TX bytes:68508 (66.9 KiB)

route -n :

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth1


lshw:

  *-network:0             
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: a
       bus info: pci@00:0a.0
       logical name: eth0
       version: 13
       serial: 00:11:2f:de:4a:98
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.9 duplex=full firmware=N/A latency=64 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:fab00000-fab03fff ioport:a800-a8ff irq:17
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@00:0b.0
       logical name: eth1
       version: 10
       serial: 00:00:c5:c1:e9:62
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:b000-b0ff iomemory:fac00000-fac000ff irq:18



I have already tried this :

brandon@brandon-desktop:~$ sudo ifdown eth1
Password:
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 5585
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:00:c5:c1:e9:62
Sending on   LPF/eth1/00:00:c5:c1:e9:62
Sending on   Socket/fallback

brandon@brandon-desktop:~$ sudo ifdown eth1
ifdown: interface eth1 not configured

brandon@brandon-desktop:~$ sudo ifdown eth0
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 11959
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:2f:de:4a:98
Sending on   LPF/eth0/00:11:2f:de:4a:98
Sending on   Socket/fallback
brandon@brandon-desktop:~$ sudo dhclient -r eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:2f:de:4a:98
Sending on   LPF/eth0/00:11:2f:de:4a:98
Sending on   Socket/fallback
brandon@brandon-desktop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:2f:de:4a:98
Sending on   LPF/eth0/00:11:2f:de:4a:98
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

brandon@brandon-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2F:DE:4A:98  
          inet6 addr: fe80::211:2fff:fede:4a98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86253 (84.2 KiB)  TX bytes:6428 (6.2 KiB)
          Interrupt:17 

eth0:avah Link encap:Ethernet  HWaddr 00:11:2F:DE:4A:98  
          inet addr:169.254.7.42  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:970 errors:0 dropped:0 overruns:0 frame:0
          TX packets:970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:76780 (74.9 KiB)  TX bytes:76780 (74.9 KiB)

brandon@brandon-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0



and this :




brandon@brandon-desktop:~$ sudo /etc/init.d/networking stop
Password:
 * Deconfiguring network interfaces...                                      RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 14631
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:2f:de:4a:98
Sending on   LPF/eth0/00:11:2f:de:4a:98
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth1.pid with pid 11221
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:00:c5:c1:e9:62
Sending on   LPF/eth1/00:00:c5:c1:e9:62
Sending on   Socket/fallback
                                                                     [ OK ]
brandon@brandon-desktop:~$ sudo modprobe -r skge
brandon@brandon-desktop:~$ sudo modprobe skge debug=16
brandon@brandon-desktop:~$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                        There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:00:c5:c1:e9:62
Sending on   LPF/eth1/00:00:c5:c1:e9:62
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
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
                                                                     [ OK ]


I dont really know what to do at this point, I would really appreciate any help, thanks in advance!

---

### Post by jingo811 on 2007-10-11
I don't know what an onboard Lan is but I recognize the word ethernet.
Are you connecting your ethernet card with a TCP/IP cable to the modem?
Is your PC connected to a router?

Try these commands in terminal.
```
$ sudo mii-tool eth0
$ sudo mii-tool eth1
$ sudo dhclient eth0
```

---

### Post by thebrandon on 2007-10-11
I am connecting from the cable modem into either the pci card or the onboard ethernet plug in.

Here are the results from what you told me to do :

(this is with the ethernet cable plugged into the onboard connection eth0)

brandon@brandon-desktop:~$ sudo mii-tool eth0
Password:
eth0: negotiated 100baseTx-FD, link ok
brandon@brandon-desktop:~$ sudo mii-tool eth1
eth1: no link
brandon@brandon-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:2f:de:4a:98
Sending on   LPF/eth0/00:11:2f:de:4a:98
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
brandon@brandon-desktop:~$ sudo dhclient eth1brandon@brandon-desktop:~$ sudo mii-tool eth0
Password:
eth0: negotiated 100baseTx-FD, link ok
brandon@brandon-desktop:~$ sudo mii-tool eth1
eth1: no link
brandon@brandon-desktop:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:11:2f:de:4a:98
Sending on   LPF/eth0/00:11:2f:de:4a:98
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
brandon@brandon-desktop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 21449
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:00:c5:c1:e9:62
Sending on   LPF/eth1/00:00:c5:c1:e9:62
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
brandon@brandon-desktop:~$ 
brandon@brandon-desktop:~$ 
brandon@brandon-desktop:~$ sudo mii-tool eth0
eth0: no link
brandon@brandon-desktop:~$ sudo mii-tool eth1
eth1: negotiated 100baseTx-FD, link ok
brandon@brandon-desktop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 21493
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:00:c5:c1:e9:62
Sending on   LPF/eth1/00:00:c5:c1:e9:62
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
brandon@brandon-desktop:~$ 

There is already a pid file /var/run/dhclient.pid with pid 21449
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:00:c5:c1:e9:62
Sending on   LPF/eth1/00:00:c5:c1:e9:62
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


HERE I SWAPPED THE CABLE OVER TO ETH1 (THE ETHERNET CARD)


brandon@brandon-desktop:~$ 
brandon@brandon-desktop:~$ 
brandon@brandon-desktop:~$ sudo mii-tool eth0
eth0: no link
brandon@brandon-desktop:~$ sudo mii-tool eth1
eth1: negotiated 100baseTx-FD, link ok
brandon@brandon-desktop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 21493
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:00:c5:c1:e9:62
Sending on   LPF/eth1/00:00:c5:c1:e9:62
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
brandon@brandon-desktop:~$ 


And still no go, same results as before.

---

### Post by donyfrosman on 2007-10-12
does anyone can help him, cause i have same problem with him

---

### Post by jingo811 on 2007-10-12
I'm out of ideas.  Are you using a router?
Are you using VPN networking where you are at?

---

### Post by thebrandon on 2007-10-12
nope, no router, and I just googled vpn because I didnt know what it was and I am pretty sure I dont have a setup like that.  Just a regular direct connection.

---

### Post by perfecttao on 2007-10-12
Just looking at your thread and it looks like both of your network cards are functioning - they just seem to be failing to pick up a DHCP address......the 169.x.x.x addresses are what is referred to as an APIPA (automatic private IP address) and are generated when no DHCP server is available.

I'm wondering what the hardware your pc is connected to is?  You would probably either need to connect to a DHCP server on your LAN or possibly specify IP details on the interface/s.

It would be helpful if you could provide more information about the envirnoment that you are connecting to....chances are it's not a Ubuntu/PC fault but simply a configuration issue...

for example, is it a corporate style network where you just connect into the LAN via a network switch.  If this is the case and there are other machines that DO work on the network check out their IP address range (terminal-ifconfig in linux or start-run-cmd-ipconfig in windows)  it may be that IP addresses are assigned manually....

What device sits between your network and the internet?

---

### Post by donyfrosman on 2007-10-12
sorry to interupt,
seem like i have same problem with thebrandon, i want to connect my laptop to LAN in my office for using the internet, i already test with win xp thats work but if i use ubuntu didn't work i make it same in configuration as i configure the network in win xp, so there is another setting that i must configure in ubuntu that in win xp doesn't have. 
thanks before

---

### Post by thebrandon on 2007-10-13
Well I finally seem to have gotten my problem fixed and I feel kinda silly that it took so long.  All I had to do was turn my computer off then unplug my cable modem for a minute or so, then plug it back in and boot up and everything worked.  It was a suggestion that I got from the #Ubuntu channel on Freenode and I think it has something to do with obtaining the Mac Adress.  Also, I am connecting with my Realtek ethernet card and before I booted back up I disabled the onboard ethernet port (the Marvell) so I still dont really know if it works or not.  Anyhow, I hope that this information is helpful to someone else who might be having similar trouble and thanks to all of you that helped me fix this problem.

---

### Post by marvinB on 2008-01-27
It's so nice when the instructions work. THANK YOU ALL

---

