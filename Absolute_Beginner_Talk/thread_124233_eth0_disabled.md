---
title: "eth0 disabled"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by Kevbb on 2006-02-01
Today I cant connect with my network....all was working OK the other day. I notice eth0 is disabled, and have tried "sudo ifup eth0" but it says interface eth0 already configured.

Help.....please!!

Kevbb

---

### Post by Sokraates on 2006-02-01
The easiest way is to select "Network" from your GNOME-Panel (I think it's under "System", but I'm not shure; don't use GNOME and right now I'm not in front of my box) and then activate it via the GUI.

Alternatively (if you'a a console fan) try
```
sudo ifconfig eth0 down
```
dolowed by
```
sudo ifconfig eth0 up
```

I've made the experience, that sometimes "ifconfig up/down" worked better than "ifup" or "ifdown".

---

### Post by alamba on 2006-02-01
if this does'nt work just post "ifconfig eth0" and "netstat -rn". Before doing that ping your router.

---

### Post by Kevbb on 2006-02-01
Didint work...but as requsted here's ifconfig eth0
```

Link encap:Ethernet HWaddr 00:10:c6:08:4c:f5
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX Packets:17 errors:0 dropped:0 overruns:0 frame:0
TX Packets:11 errors:0 dropped:0 overruns:0 carrier:0
collision:0 txcueuelen:1000
RX Bytes:2059 (2.0 kiB)   TX Bytes:3762 (3.6KiB)
interupt:11 Base address:0xe400

```
netstat -rn =
```

Kernal IP Routing table
Destination Gateway Genmask Flags MSS Window irtt iface

```
Nothing else comes up for that one...

Any help is appreciated.

Cheers Kevbb.

---

