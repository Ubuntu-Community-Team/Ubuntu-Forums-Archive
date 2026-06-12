---
title: "Can't mount Samba share on Asus 1225C"
date: 2013-03-08
forum: Any Other OS
---

### Post by damianoloan on 2013-03-08
I've been having problems with a Samba share from my Asus 1225C to my Raspberry Pi for some weeks.  The Pi can't access the share, nor can my phone, using AndSMB on an Android fork.

Forgive me, I've been using Linux Mint 13 for a few weeks while trying to resolve the problem.

The contents of my smb.conf file are here: [http://pastebin.com/1xJijthd](http://pastebin.com/1xJijthd)

ifconfig output:
```
Link encap:Ethernet  HWaddr 10:bf:48:1d:6d:93  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:50 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr e0:b9:a5:f7:9b:b2  
          inet addr:192.168.1.43  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e2b9:a5ff:fef7:9bb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9011 errors:3 dropped:0 overruns:0 frame:10717
          TX packets:8906 errors:27 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6824232 (6.8 MB)  TX bytes:1389243 (1.3 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100832 (100.8 KB)  TX bytes:100832 (100.8 KB)
```

---

### Post by Perfect Storm on 2013-03-09
Thread moved to Other OS/Distro Talk.

---

