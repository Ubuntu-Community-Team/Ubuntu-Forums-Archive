---
title: "Network problems"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Maleficus on 2006-08-06
Hi, I just switched to Ubuntu and I am trying to get my internet connection to work, I connect through a SMC 7004ABR router, the nic is a 3-com 3c905C TX nic which has worked fine until i installed Ubuntu. After a little digging around I tried a couple of things to no avail, I believe this is the pertinent information so that hopefully you guys can help me fix this problem.


maleficus@MaryJane:~$ sudo mii-tool eth0
eth0: 100 Mbit, full duplex, no link
maleficus@MaryJane:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:01:03:BB:53:24
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0x8000

maleficus@MaryJane:~$ lspci | grep Eth
0000:01:09.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)
maleficus@MaryJane:~$ lsmod | grep mii
mii                     5888  1 3c59x

Obviously the problem is the 'no link' part but I don't know why it won't grab a link, I've done dhclient and it doesn't grab anything then says its sleeping :(

I've tried it connected the router (as in the computer im posting this from right now) and I've tried it connected directly to the Modem, hasn't made a difference yet.

I'll be messing with this all day so any help given will be greatly appreciated.

---

### Post by cantormath on 2006-08-06
> **Maleficus said:**
> Hi, I just switched to Ubuntu and I am trying to get my internet connection to work, I connect through a SMC 7004ABR router, the nic is a 3-com 3c905C TX nic which has worked fine until i installed Ubuntu. After a little digging around I tried a couple of things to no avail, I believe this is the pertinent information so that hopefully you guys can help me fix this problem.


maleficus@MaryJane:~$ sudo mii-tool eth0
eth0: 100 Mbit, full duplex, no link
maleficus@MaryJane:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:01:03:BB:53:24
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:209 Base address:0x8000

maleficus@MaryJane:~$ lspci | grep Eth
0000:01:09.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)
maleficus@MaryJane:~$ lsmod | grep mii
mii                     5888  1 3c59x

Obviously the problem is the 'no link' part but I don't know why it won't grab a link, I've done dhclient and it doesn't grab anything then says its sleeping :(

I've tried it connected the router (as in the computer im posting this from right now) and I've tried it connected directly to the Modem, hasn't made a difference yet.

I'll be messing with this all day so any help given will be greatly appreciated.

have you tried: 
```
sudo dhclient eth0
```

---

### Post by Maleficus on 2006-08-06
Yes, I have done sudo dhclient eth0 and it yieled no results, thanks for the quick reply, upon further examination I think the problem may be the 100mbit link speed, my cable is crappy/router idk but i've always had to set my linkspeed to 10mbit full duplex in windows so that might be it here as well, although I don't know how to do that so if anyone could inform me that would be great. let me swap up cables and go do dhclient again so i can paste the actual results, thanks again for the quick reply

Here is the resulting text from sudo dhclient eth0:

maleficus@MaryJane:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:01:03:bb:53:24
Sending on   LPF/eth0/00:01:03:bb:53:24
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Maleficus on 2006-08-06
Alright, the problem is indeed the cable, its apparently 10mbit

I am posting from my ubuntu box now with a 100mbit cable but it doesn't really reach :P

can anyone inform me how to set my nic card to use 10mbit full duplex instead of 100mbit?

got it

sudo ethtool -s eth0 speed 10 duplex full  FTW

Thanks Cantorman

---

