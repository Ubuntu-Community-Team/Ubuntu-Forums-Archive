---
title: "lan problems in New Gutsy"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by Carlos Malaga on 2007-11-24
I am totaly new to Ubuntu.  I installed Gutsy (7.10) 0n my HP Pavilion FX145.  I can't connect to the LAN.  The port is in the motherboard and is recognized in device manager as net.80203, but I can't get it to work.  Do I need a driver or what?  How do I go about this?  Help much appreciated. :confused:

---

### Post by Taboo Mirage on 2007-11-24
Please paste the output of the following command, which may help with debugging this issue:

```
sudo ifconfig
```

---

### Post by Carlos Malaga on 2007-11-24
run the ifconfig.  Since no internet connection is available I transcribe 

eth0   Link encap:Ethernet  HWaddr 00:C0:9F:06:D1:5E
[INDENT]inet6 addr: fe80::2c0:9fff:fe06:d15e/64 Scope:Link
UP BROADCAST RUNNING MULTICAST   MTU:1500   Metric:1
RX packets:272  errors:0  dropped:0  Overruns:0 frame:0
TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:38856 (37.9 KB) TX bytes:20518 (20.0KB)
Interrupt:11 Base address:0xe800[/INDENT]

eth0:avah Link encap:Ethernet HWaddr: 00:C0:9F:06:D1:5E
[INDENT]inet addr:1169.254.7.43 Bcast:169.254.255.255 Mask 255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 metric:1
Interupt:11 Base address:0xe800
[/INDENT]

lo         Link encap:local Loopback
[INDENT]inet addr:127.0.0.1 Mask: 255.0.0.0
inet6 addr:  ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1`
RX packets:192 errors:0 dropped:0 overruns:0 frame:0
TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txquelen:0
RX bytes:14620 (14.2 KB)  TX bytes:14620 (14.2 KB)[/INDENT]

All I notice is I am getting no IP address on the eth0

Thanks for your help

---

