---
title: "Wlanassistant connects to network, but can't access the internet"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by tartarian on 2007-01-21
Hey, I've just upgraded to Edgy 6.10, and I can't connect to my wireless internet connection. I used wlanassistant on Dapper and it worked fine but now it doesn't. I read a bug report on this app on the 'known issues' of kubuntu, but it said a fix had been made and i just needed to upgrade it. 

Before I downloaded the update, wlanassistant wouldn't connect at all, but after the update it tells me that it's connected; however I can't connect to any internet sites and ping outputs 'unknown host' to google.com

I copied my /etc/network/interfaces file from the working Dapper installation before I upgraded, and i've copied that into /etc/network/interfaces but it still doesn't display anything. 

Any ideas?

thankyou!

---

### Post by shane634 on 2007-01-21
A little more info is needed here. What wireless card are you using? What is the chipset? Post those and it may be a little easier for us t o help you.

---

### Post by houstonbofh on 2007-01-21
Also post the results of an 'ifconfig' because it sounds like you are not getting an IP address.

---

### Post by tartarian on 2007-01-21
Sorry! My Laptop is an Packard Bell Easynote R4250 with a built in wireless card - Billionton 802.11b/g Mini-PCI Wireless LAN adapter (according to the website :D)

the output of ifconfig is :
```

eth0      Link encap:Ethernet  HWaddr 00:40:D0:70:C1:19
          inet addr:192.168.1.99  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:d0ff:fe70:c119/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:267579 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:398756420 (380.2 MiB)  TX bytes:11241823 (10.7 MiB)
          Interrupt:3 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14887 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14887 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3593351 (3.4 MiB)  TX bytes:3593351 (3.4 MiB)

ra0       Link encap:Ethernet  HWaddr 00:10:60:0C:D3:00
          inet addr:192.168.1.24  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:60ff:fe0c:d300/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:186325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:285296 errors:2272 dropped:2272 overruns:0 carrier:0
          collisions:7062 txqueuelen:1000
          RX bytes:280601538 (267.6 MiB)  TX bytes:20385826 (19.4 MiB)
          Interrupt:11

```
and the output of iwconfig is :
```

lo        no wireless extensions.

ra0       RT2500 Wireless  ESSID:"WANADOO-3EB4"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:0E:9B:A2:14:1C
          Bit Rate:54 Mb/s   Tx-Power:0 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=50/100  Signal level=-92 dBm  Noise level:-211 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

```
I manually set the access point of ra0 myself, and it still didn't work. 

Any ideas?

Thankyou!!!!

---

