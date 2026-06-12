---
title: "Internet connection sharing"
date: 2011-01-29
forum: Apple Hardware Users
---

### Post by DARKAD on 2011-01-29
I'm trying to share the internet connection from a Mac os X.

I've got a huawei usb internet connection and an ubuntu 10.04 pc connected through the ethernet cable.

On the mac preference pane, the "internet sharing" is on.

**mac ifonfig**:
```

en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	ether 00:22:41:35:40:ed 
	inet 192.168.2.1 netmask 0xffffff00 broadcast 192.168.2.255
	media: autoselect (100baseTX <full-duplex>)
	status: active

```

**ubuntu ifconfig**:
```

eth0      Link encap:Ethernet  HWaddr 00:40:f4:89:d5:8f  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe89:d58f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2423 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13968 (13.9 KB)  TX bytes:236439 (236.4 KB)
          Interrupt:22 Base address:0xd800 

```

---

### Post by DARKAD on 2011-01-29
I solved running dhcpclient on ubuntu.

---

