---
title: "Occasional On-line Problem"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by yad39 on 2008-01-31
I have had Ubuntu 7.10 now for 3 weeks and occasionally when trying to get on-line I get a 	message page appear informing me 'Server not found'.

This is occurring about 50% of the time. Restarting the computer doesn't seem to cure but restarting & powering down computer & modem improves my chance's.

Its as if 7.10 cant always 'Auto Detect' my modem. 

Thanks to anyone who can help....

---

### Post by jan quark on 2008-01-31
OK 
some input

pls post the results of the following terminal commands
```

ifconfig
```
```
iwconfig
```
```
lspci
```
[HTML]sudo iwlist scan < here you have to enter the login password[/HTML]

---

### Post by yad39 on 2008-01-31
ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0B:DB:C2:8D:ED  
          inet6 addr: fe80::20b:dbff:fec2:8ded/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12793 (12.4 KB)  TX bytes:492 (492.0 b)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr 00:16:E3:64:57:12  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e3ff:fe64:5712/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2053 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1704 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2135495 (2.0 MB)  TX bytes:236137 (230.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.


lspci

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:05.0 Communication controller: Conexant Unknown device 2702 (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.


Hope this helps...

.

---

### Post by jan quark on 2008-01-31
can you please post the exact name of your modem?

---

### Post by jan quark on 2008-01-31
[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

perhaps this is the right guide for you

> 01:05.0 Communication controller: [COLOR="Red"]Conexant Unknown device [/COLOR]2702 (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

---

### Post by yad39 on 2008-01-31
Modem is a:

 BT Voyager 220V ADSL Voice Router

---

### Post by jan quark on 2008-01-31
voyager?

then try this guide
[http://ubuntuforums.org/showthread.php?t=140010](http://ubuntuforums.org/showthread.php?t=140010)

---

