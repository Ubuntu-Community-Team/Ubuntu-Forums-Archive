---
title: "Pro/Wireless 2200 driver- how do i know it's installed?"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by deafchickadee on 2007-03-20
self explanatory title. How do i find out the driver is installed?
If I dont have it, how to i get it installed? 

I have already installed the Windows Wireless driver thingy, but not the specific ini file. I have already installed ndisswrapper and network manager.

Hints anyone? THank you!!!!

---

### Post by deafchickadee on 2007-03-20
for your info..  i did this

```
ella@ella-laptop:~$ sudo apt-get install wifi-radar
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  wifi-radar
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 37.3kB of archives.
After unpacking 213kB of additional disk space will be used.
Get:1 http://au.archive.ubuntu.com edgy/universe wifi-radar 1.9.7-0ubuntu2 [37.3kB]
Fetched 37.3kB in 3s (12.0kB/s)         
Selecting previously deselected package wifi-radar.
(Reading database ... 107280 files and directories currently installed.)
Unpacking wifi-radar (from .../wifi-radar_1.9.7-0ubuntu2_all.deb) ...
Setting up wifi-radar (1.9.7-0ubuntu2) ...

ella@ella-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:6B:57:C1  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe6b:57c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1632841 (1.5 MiB)  TX bytes:296342 (289.3 KiB)
          Interrupt:10 

eth1      Link encap:Ethernet  HWaddr 00:16:6F:36:1B:A9  
          inet6 addr: fe80::216:6fff:fe36:1ba9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:8662 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1143 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0x2000 Memory:e0206000-e0206fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:500 (500.0 b)  TX bytes:500 (500.0 b)

```

---

### Post by raublekick on 2007-03-20
The ipw2200 driver should be installed by default. It is for me, at least. 

If you aren't sure, you can try the method above, or try:

modprobe ipw2200    (might need sudo to do this one)

or 

lsmod | grep ipw2200

---

### Post by deafchickadee on 2007-03-20
ella@ella-laptop:~$ lsmod | grep ipw2200
ipw2200               115652  0 
ieee80211              35272  1 ipw2200


does this mean anything?

---

