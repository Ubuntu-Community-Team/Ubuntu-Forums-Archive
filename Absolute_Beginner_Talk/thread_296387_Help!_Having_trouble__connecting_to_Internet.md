---
title: "Help! Having trouble  connecting to Internet"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by ednavarro on 2006-11-09
Hi All, 

I am new to linux and I am having trouble connecting to the internet. I'm using Comcast and I am connecting directly to my cable modem which is a Linksys.  Any help would be greatly appreciated.

---

### Post by dbott67 on 2006-11-09
Can you post the output of the following commands:
```
cat /etc/network/interfaces
```
```
ifconfig -a
```

Thanks,
Dave

---

### Post by Najand on 2006-11-09
Hmm, can you copy and paste the out put of "ifconfig" here?

---

### Post by ednavarro on 2006-11-09
I'm away from my linux machine at this time I will post my results later today. Thank you for your help!

---

### Post by ednavarro on 2006-11-09
I'm away from my linux machine at this time I will post my results later today. Thank you for your help! I really appreciate the help! Also my Apologies for not being able to provide the request information.

---

### Post by mkuperus on 2006-11-09
I am having the same problem with 6.10.

I can see my local network but anything beyond that is turns up nothing.  I've tried to ping other sites by IP and nameserver but no response.

```
auto eth0
iface eth0 inet dhcp

```

I am assigned a local IP address by the router as well as the appropiate DNS entries.

---

### Post by dbott67 on 2006-11-09
mkuperus,

Can you post the output of:
```
route -n
```
as well as
```
ifconfig -a
```

Thanks,
Dave

---

### Post by mkuperus on 2006-11-09
After rebooting one of my other machines I found that some of my router settings had been lost so new connections were not being enabled.  Everything is working fine now.  Probably not the solution for others but worth looking into.

---

### Post by ednavarro on 2006-11-10
This is what I get when I type cat /etc/network/interfaces

auto lo

iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

This is what I got when i typed ifconfig -a 

eth2 Link encap: Ethernet Hwaddr 00:05:5D:CD:E2:EC
     Inet6 addr: fe80::205:5dff:fecd:e2ec/64 Scope:link
     Up broadcast Running Multicast MTU:1500 Metric:1
     RX packets:10634 errors:0 dropped:0 overruns:0 frame:0
     TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
     Rx bytes:694028(677.7 KiB) Tx bytes:4230 (4.1 KiB)
     Interrupt: 217 Base address: 0X8000

lo   Link encap:local loopback
     inet addr:127.0.0.1 Mask: 255.0.0.0
     inet6 addr: ::1/128 scope:host
     up loopback running  mtu:16436 metric:1
     Rx:149 errors:0 dropped:0 overruns:0 frame:0
     TX packets:149 errors:0 dropped:0 overruns:0 carrier:0
     collisions: 0
     Rx bytes: 11200(10.9KiB) Tx bytes: 11200(10.9 KiB)

Sit0 Link encap: IPv6-in-IPv4
     NOARP mtu:1480 metric:1

---

### Post by ebozzz on 2006-11-10
I also use Comcast and had no problems connecting. All I did was connect the cable to my Ethernet card, reset the modem, complete the install, reboot the PC and I was online without any configuration changes. Even on PCs where I did the install prior to connecting to the internet I was able to get online without any problems. In those instances, I just connected the cable to the NIC card, reset the modem then booted the PC. I honestly have never had  as easy an install as I have had with Ubuntu. I am using an RCA DCM315 cable modem and my network is wired.

---

### Post by dbott67 on 2006-11-10
As ebozzz metnions, make sure you reset the modem (there may be a little button on the back or just unplug the power for a few minutes).

**_If not, try these  commands:_**

To de-activate the interface, type:
```
sudo ifdown eth2
```

To re-activate the interface, type:
```
sudo ifup eth2
```

To request an IP from the DHCP server, type:
```
sudo dhclient eth2
```

-Dave

---

