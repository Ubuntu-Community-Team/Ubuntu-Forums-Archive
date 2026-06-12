---
title: "Wireless USB donlge not working"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by yonexFactory on 2007-03-30
Hey... first post here, whoohoo!

I've been searching everywhere for a fix to this, but I can't seem to find it. I've got a (no-name?) 802.11g/b WLAN USB stick that I'm trying to use in an old laptop that I just installed Ubuntu on not too long ago (which means I'm a bit of a Linux noob...). I got it off eBay and made sure it came with an install CD with the hope that I could just install the .inf file from the CD using ndiswrapper. But, of course, there was no .inf file, and Wine obviously does nothing with the setup.exe. Needless to say, I can't get this thing working at all, and I can't find any drivers that work. (I've played around with /etc/network/interfaces too.)

lsusb gives:

Bus 003 Device 003: ID 124a:4023 AirVast 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

ifconfig gives:

eth0      Link encap:Ethernet  HWaddr 00:50:EB:04:2C:21  
          inet addr:65.110.239.29  Bcast:65.110.239.255  Mask:255.255.254.0
          inet6 addr: 2002:416e:ef30:1:250:ebff:fe04:2c21/64 Scope:Global
          inet6 addr: fe80::250:ebff:fe04:2c21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:132162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11587 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43732994 (41.7 MiB)  TX bytes:1546286 (1.4 MiB)
          Interrupt:5 Base address:0xd400 

eth1      Link encap:Ethernet  HWaddr 00:0A:E9:10:1A:C3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1496 (1.4 KiB)  TX bytes:1496 (1.4 KiB)

and iwconfig gives:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Channel=1  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Sorry for the long post, I'm just trying give as much info as I can. Any tips would be very appreciated... Please help!

Thanks

---

### Post by digital_sabotage on 2007-03-30
i'm near noob but it looks like your wireless adapter is an "AirVast"  ...i would probably work on finding a driver that isn't an executable ...or just the .inf file perhaps ...just a thought ...good luck

---

### Post by yonexFactory on 2007-03-30
Yeah, I've tried numerous drivers from Google searches but none of them have worked.

---

### Post by yonexFactory on 2007-03-31
Anyone know if I can use the .sys file from system32/DRIVERS from my Windows machine?

---

