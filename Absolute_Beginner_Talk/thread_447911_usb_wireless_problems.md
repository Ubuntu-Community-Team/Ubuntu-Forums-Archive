---
title: "usb wireless problems"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by clvnhbbs5 on 2007-05-18
i just installed ubuntu yesterday and spent the rest of the day rying to connect to a wep network using a linksys usb device. it will detect the networks but will not connect. it wont even connect to an open network. i have searched the web for different drivers and one have worked. i am at a loss of ideas, pleas help.

---

### Post by chamberlain2006 on 2007-05-18
Hello.  I need to know a few things:
a) what driver are you using?
b) what is the output of iwconfig, ifconfig
c) do you get error messages when you try to connect?

---

### Post by clvnhbbs5 on 2007-05-18
i am using the default driver now, i reinstalled ubuntu after i thought i messed it up.



iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

rausb1    RT2500USB WLAN  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:18:F8:4A:3C:35   
          Bit Rate=36 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=62/100  Signal level:-86 dBm  Noise level:-206 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0A:E6:EE:1D:EA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:746 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:59604 (58.2 KiB)  TX bytes:59604 (58.2 KiB)

rausb1    Link encap:Ethernet  HWaddr 00:12:17:88:35:A9  
          inet6 addr: fe80::212:17ff:fe88:35a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11148768 (10.6 MiB)  TX bytes:135348 (132.1 KiB)

and no errors when i try to connect.

---

### Post by chamberlain2006 on 2007-05-18
It seems to be sending and receiving packages...but it doesn't have an IP address.  Try doing
```
sudo ifdown rausb1; sudo ifup rausb1
```
I'm just trying to find some info on Google.

---

### Post by clvnhbbs5 on 2007-05-18
ifdown: interface rausb1 not configured
Ignoring unknown interface rausb1=rausb1.

this is what i got

---

### Post by chamberlain2006 on 2007-05-18
Here's a thought ... what's the output of 
```
cat /etc/network/interfaces
```

---

### Post by clvnhbbs5 on 2007-05-18
auto lo
iface lo inet loopback


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by chamberlain2006 on 2007-05-18
Aha!  That's the culpret!  You haven't configured your interface.  You need to configure it through System>Administration>Network.

---

### Post by clvnhbbs5 on 2007-05-18
ok. what am i supposed to do there?

---

### Post by chamberlain2006 on 2007-05-18
You need to type in your settings.  IE, your ESSID, WEP/WPA info (if needed), and DHCP

---

### Post by clvnhbbs5 on 2007-05-18
ok so i did that and it tells me there is 0% sgnal comming from the connection

---

### Post by chamberlain2006 on 2007-05-18
Can you repost the output of the things i said in my first post?

---

### Post by clvnhbbs5 on 2007-05-18
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

rausb1    RT2500USB WLAN  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:18:F8:4A:3C:35   
          Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=62/100  Signal level:-86 dBm  Noise level:-206 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0A:E6:EE:1D:EA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63940 (62.4 KiB)  TX bytes:63940 (62.4 KiB)

rausb1    Link encap:Ethernet  HWaddr 00:12:17:88:35:A9  
          inet6 addr: fe80::212:17ff:fe88:35a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13587940 (12.9 MiB)  TX bytes:152802 (149.2 KiB)

---

### Post by chamberlain2006 on 2007-05-18
And what's your /etc/network/interfaces now?

---

### Post by clvnhbbs5 on 2007-05-18
auto lo
iface lo inet loopback


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp








iface rausb1 inet dhcp
wireless-essid motorola 0F0
wireless-key *********

auto rausb1

---

### Post by chamberlain2006 on 2007-05-18
Your network is called "motorola 0F0"... that seems a little suspicious, are you sure that's right?

---

### Post by clvnhbbs5 on 2007-05-18
yea thats the right one. i have it working on my widows laptop.

---

### Post by chamberlain2006 on 2007-05-18
Hmmmm.  Try doing ```
sudo ifdown rausb1; sudo ifup rausb1
``` again, now that your settings are right.

---

### Post by clvnhbbs5 on 2007-05-18
ifdown: interface rausb1 not configured
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/rausb1/00:12:17:88:35:a9
Sending on   LPF/rausb1/00:12:17:88:35:a9
Sending on   Socket/fallback
DHCPDISCOVER on rausb1 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.10.1
DHCPREQUEST on rausb1 to 255.255.255.255 port 67
DHCPACK from 192.168.10.1
bound to 192.168.10.4 -- renewal in 38535 seconds.

---

### Post by chamberlain2006 on 2007-05-18
Congrats, you should be connected!  Try navigating to a page and check the results!

---

### Post by clvnhbbs5 on 2007-05-18
thank you so much. you are the best

---

### Post by chamberlain2006 on 2007-05-18
No problem, we're here to help.  Let me know if you have any other problems with it!

---

