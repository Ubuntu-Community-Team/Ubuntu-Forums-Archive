---
title: "Wireless can see internal network, but no internet"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by lazyart on 2007-05-20
Hey folks,

Just installed Feisty on a Compaq N620c notebook.  Installed a PCMCIA Cisco wifi card.  Entered my connection info and with DHCP I'm getting an IP address.  Can ping machines inside the network.  It will even resolve external addresses but I cannot load pages or even receive responses from external sites.

My network has been running for 2 years now with 4 wireless clients, all receiving addresses by DHCP so the network is configured correctly.

Am using the restricted driver (have no choice but to).  Card shows up as ath0 (atheros chipset) and also exposes wifi0 with which I don't know what to do.

Any ideas?  When connected by wire I have full connectivity.

---

### Post by rich.bradshaw on 2007-05-20
what's the result of ifconfig and iwconfig?

Have you got a weird proxy in Firefox?

Try using lynx from the command line, it's a text only browser, but if that works, it narrows it down a bit!

lynx [www.google.com](www.google.com)

---

### Post by rich.bradshaw on 2007-05-20
Actually, don't think Lynx is installed by default...

can you do

sudo apt-get update 

successfully?

---

### Post by lazyart on 2007-05-20
Well, I am able to post this only because I switched from DHCP to static.

Here is my ifconfig:```
ath0      Link encap:Ethernet  HWaddr 00:40:96:A9:BC:89  
          inet addr:10.10.10.157  Bcast:10.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::240:96ff:fea9:bc89/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3643 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6599658 (6.2 MiB)  TX bytes:257997 (251.9 KiB)

eth0      Link encap:Ethernet  HWaddr 00:02:A5:C3:D5:4E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

wifi0     Link encap:UNSPEC  HWaddr 00-40-96-A9-BC-89-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13299 errors:0 dropped:0 overruns:0 frame:398
          TX packets:3828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:7765112 (7.4 MiB)  TX bytes:375469 (366.6 KiB)
          Interrupt:10
```and here is iwconfig:```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"blue"  Nickname:""
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:11:50:67:8D:1D   
          Bit Rate:24 Mb/s   Tx-Power:16 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=36/94  Signal level=-59 dBm  Noise level=-95 dBm
          Rx invalid nwid:1874  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I disabled ipv6 in firefox but it didn't help.  When wired everything works aok, it's the same network via dhcp.  When I go to the air it works only if I go static.

---

### Post by lazyart on 2007-05-21
Bump.  And there is no proxy (home installation).

---

