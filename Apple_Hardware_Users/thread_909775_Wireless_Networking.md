---
title: "Wireless Networking"
date: 2008-09-03
forum: Apple Hardware Users
---

### Post by Qloor on 2008-09-03
I still can't connect my MacBook wireless after two days of trying. I want to use Wifi-Radar (if possible, it's already installed) to get online. I'm using a new MacBook and have no idea how to do this. I'm new to Ubuntu so don't hesitate to heavily explain things.

---

### Post by cyberdork33 on 2008-09-03
> **Qloor said:**
> I still can't connect my MacBook wireless after two days of trying. I want to use Wifi-Radar (if possible, it's already installed) to get online. I'm using a new MacBook and have no idea how to do this. I'm new to Ubuntu so don't hesitate to heavily explain things.
See the "Before you post" link in my signature and identify your hardware and find the wiki page you need to get the wireless driver installed. If you have already tried what is instructed there, please post what you did and exactly what the issue is (errors? Can you see APs?)

---

### Post by capnahab on 2008-09-04
I have the same problem wih a macbook 2.1
Same problem. I have used Synaptic to install the ath9k driver to a macbook 2.1.

I have the ath9k installed in the hardware drivers and in use. In Wicd I can see the netwrok but not connect using either DHCP or static Ip.
Ifconfig and lsmod |grep ath9 are below.

capn@capn-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:63:34:f2:23  
          inet addr:192.168.3.14  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:63ff:fe34:f223/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2963 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2296085 (2.1 MB)  TX bytes:359360 (350.9 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:170000 (166.0 KB)  TX bytes:170000 (166.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:b3:bb:dc:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1c:b3:bb:dc:04  
          inet addr:169.254.7.56  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-B3-BB-DC-04-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

capn@capn-laptop:~$ lsmod |grep ath9
ath9k                 285368  0 
mac80211              258560  1 ath9k
capn@capn-laptop:~$

---

### Post by cyberdork33 on 2008-09-04
Can you run 'sudo dhclient' after you have tried associating with an AP and post the output?

---

### Post by Qloor on 2008-09-04
> **capnahab said:**
> I have the same problem wih a macbook 2.1
Same problem. I have used Synaptic to install the ath9k driver to a macbook 2.1.

I have the ath9k installed in the hardware drivers and in use.

@cyberdork: I've also done this. Not working. I have a new MacBook, though.

Edit: I'm also using hardy. Should I try and use an earlier version?

---

### Post by capnahab on 2008-09-04
sudo dhclient is 

capn@capn-laptop:~$ sudo dhclient
There is already a pid file /var/run/dhclient.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1c:b3:bb:dc:04
Sending on   LPF/wlan0/00:1c:b3:bb:dc:04
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:1b:63:34:f2:23
Sending on   LPF/eth0/00:1b:63:34:f2:23
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPREQUEST of 192.168.3.14 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.3.14 from 192.168.3.1
bound to 192.168.3.14 -- renewal in 39870 seconds.
capn@capn-laptop:~$

---

### Post by cyberdork33 on 2008-09-04
> **capnahab said:**
> ```

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPREQUEST of 192.168.3.14 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.3.14 from 192.168.3.1
bound to 192.168.3.14 -- renewal in 39870 seconds.
```

It looks like you got an IP.

---

### Post by Qloor on 2008-09-04
> **Qloor said:**
> @cyberdork: I've also done this. Not working. I have a new MacBook, though.

Edit: I'm also using hardy. Should I try and use an earlier version?

One last thing, I'm running on i386 apparently, but is their any way to install the drivers (if needed) or do anything else I might need to do to wirelessly connect without accessing the internet. I have two computers but no ethernet cord so I can't get online off of my Ubuntu Mac, but I can transfer things.

---

### Post by capnahab on 2008-09-04
hmmm, so it would seem . However, firefox can't connect to anything and i can't ping 
Ifconfig gives me an ip address as below, but its not in the usual range I get from my apple airport, which I have set up to share a single IP.

I wonder if its my DNS (which should be from DHCP ?.

capn@capn-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:63:34:f2:23  
          inet6 addr: fe80::21b:63ff:fe34:f223/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10557 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6519 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8466038 (8.0 MB)  TX bytes:1089065 (1.0 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3415 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3415 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:171349 (167.3 KB)  TX bytes:171349 (167.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:b3:bb:dc:04  
          inet6 addr: fe80::21c:b3ff:febb:dc04/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10396 (10.1 KB)  TX bytes:38131 (37.2 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1c:b3:bb:dc:04  
          inet addr:169.254.7.56  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-B3-BB-DC-04-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

capn@capn-laptop:~$

---

### Post by capnahab on 2008-09-04
Also , -wicd (1.4.2 ) says I am not connected !!.

---

### Post by NeoIce on 2008-09-04
I'm having this exact same problem using ndiswrapper on a BCM4328, Macbook3,1.

I can get a DHCP lease, but no ACTUAL connectivity (via ping, browsing, et al.)

I feel like it might be a problem with wpa_supplicant since I have 1 wireless router and 2 wireless extenders, but thats a shot in the dark. I really have no idea how to even investigate this problem further.

---

### Post by cyberdork33 on 2008-09-04
> **NeoIce said:**
> I'm having this exact same problem using ndiswrapper on a BCM4328, Macbook3,1.

I can get a DHCP lease, but no ACTUAL connectivity (via ping, browsing, et al.)

I feel like it might be a problem with wpa_supplicant since I have 1 wireless router and 2 wireless extenders, but thats a shot in the dark. I really have no idea how to even investigate this problem further.
You wouldn't be able to contact the DHCP server if you were not 'connecting' wirelessly first. I think it is an issue with network-manager / wicd (or maybe even the underlying Ubuntu networking system...)

---

