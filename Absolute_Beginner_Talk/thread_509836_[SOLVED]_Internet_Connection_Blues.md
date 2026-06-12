---
title: "[SOLVED] Internet Connection Blues"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by ebediel on 2007-07-25
I've been working for two weeks trying to get my connection up and running again.  I had Xubuntu on my computer and the connection worked fine.  We had a T-storm go through and the power went off.  When my computer came back up the OS was messed up.  I reloaded Xubuntu on it, everything worked except for the internet.  When I hit FFox it comes up with server not found.  I read through several threads and tried nearly everything they said but to no avail.  My computer skills are poor but I'm learning.  My Linux skills are even worse but I like Ubuntu.  BTW, I went ahead and loaded Ubuntu up on the system hoping the extra bells and whistles would help me find the problem but no.

I have a cable modem and a linksys router.  I have an ethernet connection. I have a laptop with XP that is connected to the same router with Wifi and it works good.  I using it to type this forum thread.  I will have to retype all the things from my desktop so here it goes.

ifconfig:

eth0                 Link encap:Ethernet   HWaddr 00:07:95:2E:8E:44
                        inet addr:169.254.7.13    Bcast:169.254.255.255  Mask:255.255.0.0
                        UP  BROADCAST  MULTICAST   MTU:1500   Metric:1
                        RX packets:0  errors:0  dropped:0  overruns:0  frame:0
                        TX packets:0  errors:0  dropped:0  overruns:0  carrier:0
                        collisions:0  txqueuelen:1000
                        RX  bytes:0  (0.0 b)   TX  bytes:0  (0.0 b)
                        Interrupt:11  Base  address:0xd400

eth1                 Link encap:Ethernet   HWaddr 00:08:A1:62:87:80
                        inet6  addr: fe80::208alff:fe62:8780/64  Scope:Link
                        UP  BROADCAST RUNNING  MULTICAST   MTU:1500   Metric:1
                        RX packets:0  errors:0  dropped:0  overruns:0  frame:0
                        TX packets:511  errors:0  dropped:0  overruns:0  carrier:0
                        collisions:0  txqueuelen:1000
                        RX  bytes:0  (0.0 b)   TX  bytes:0  (0.0 b)
                        Interrupt:5  Base  address:0xd000

eth1:avah       Link encap:Ethernet   HWaddr 00:08:A1:62:87:80
                        inet addr:169.254.7.13    Bcast:169.254.255.255  Mask:255.255.0.0
                        UP  BROADCAST  MULTICAST   MTU:1500   Metric:1
                        Interrupt:5  Base  address:0xd000

lo                     Link encap:Local  Loopback
                        inet addr:127.0.0.1    Mask:255.0.0.0
                        inet6  addr:  ::1/128  Scope:Host
                        UP  LOOPBACK  RUNNING   MTU:16436   Metric:1
                        RX packets:959  errors:0  dropped:0  overruns:0  frame:0
                        TX packets:959  errors:0  dropped:0  overruns:0  carrier:0
                        collisions:0  txqueuelen:0
                        RX  bytes:75223  (73.4 KiB)   TX  bytes:75223  (73.4 KiB)


I also ran: sudo dhclient

here is what I got:

There is already a pid file /var/run/dhclient.pid with pid  -1074255980
Internet Systems Consortium  DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info. please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on      LPF/eth1/00:08:A1:62:87:80
Sending on       LPF/eth1/00:08:A1:62:87:80
Listening on      LPF/eth0/00:07:95:2E:8E:44
Sending on       LPF/eth0/00:07:95:2E:8E:44
Sending on       Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I also ran: sudo pppoeconf
This is what I got from this:

SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address

Any help will be appreciated.  I will let you know up front I will probably need step by step instructions to work with.  Thanks in advance.

---

### Post by lsutiger on 2007-07-25
Have you tried to connect the desktop directly to the modem? What about changing the ethernet card? It coulda got a jolt and fried something.

---

### Post by ebediel on 2007-07-26
Yes, I went ahead and tried connecting the modem directly to the ethernet connection.  Nothing.  Then I decided to connect the modem directly to the computer via usb still no connection.  This leads me to believe that it is probably a software not a hardware problem (maybe?)

I did think about the new card option I'd like to save the money if I can, but that is a viable option.

---

### Post by ebediel on 2007-07-26
When I connected directly to the ethernet card I did restart the computer.  Same again with the usb.  The Network Manager Applet when I left click on it shows the ethernet card and the usb connection.  I had placed the eth1 connection on roaming mode.  This caused the Network Manager Applet to identify the ethernet card eth1  and the usb connection at eth2.

---

### Post by Wim Sturkenboom on 2007-07-26
At least one issue I see: your eth0 has the same address as eth1. So the computer does not know where to go with data and might well send it to the wrong interface.

Do you have 2 interfaces in your box? If so, disable one and hook the router or modem to the other one.

---

### Post by ebediel on 2007-07-26
No I only have one connection from my router to my computer.

---

### Post by ebediel on 2007-07-26
I tried another command in my terminal: route

Here's what I got:

Kernel  IP  routing  table
Destination          Gateway                Genmask                      Flags     Metric    Ref        Use   Iface
link-local               *                            255.255.0.0                U           0            0                0   eth1
link-local               *                            255.255.0.0                U           0            0                0   eth0
default                 *                            0.0.0.0                        U           1000      0                0   eth1

Appreciate any thoughts or insights.
Thanks in advance.

---

### Post by ebediel on 2007-07-26
thanks I did actually find another ethernet port on my tower and what do you know it happened to be eth0 and it connected automatically and immediately.  Glory to God and thanks to you Mr. Sturkenboom.
Problem resolved.

---

### Post by Wim Sturkenboom on 2007-07-26
Great. Please edit your opening post in advanced mode and add '[Solved]' to the title.

---

