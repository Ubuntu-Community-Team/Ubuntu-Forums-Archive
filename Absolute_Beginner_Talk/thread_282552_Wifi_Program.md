---
title: "Wifi Program"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-10-22
What is a good program to manage my wifi connection? Also, how do I check what wifi model to I have. Also, how do I check what my MAC address is?

---

### Post by GStubbs43 on 2006-10-22
For the program, enter this into the terminal:
```
sudo aptitude install wifi-radar
```
That's the program I like...

For yor MAC address:
```
sudo ifconfig -a
```
then the HWaddr part of the output is your MAC address.

---

### Post by Marsolin on 2006-10-22
I use [KNetworkManager]("http://linuxappfinder.com/package/knetworkmanager") and really like it, but if you are a Gnome user I'd try [WiFi Radar]("http://linuxappfinder.com/package/wifi-radar").

---

### Post by amitroy5 on 2006-10-22
eth1      Link encap:Ethernet  HWaddr 00:13:02:A0:E1:6A
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fea0:e16a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1738691 errors:10 dropped:272548 overruns:0 frame:0
          TX packets:1427352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1364464841 (1.2 GiB)  TX bytes:529132272 (504.6 MiB)
          Interrupt:177 Base address:0xc000 Memory:dfdff000


I get that output, but I am not sure which one is my mac address.

---

### Post by Marsolin on 2006-10-23
Where it says HWAddr is the MAC address.

---

### Post by RaverDK on 2006-10-23
Just like Marsolin says, the party whit HWaddr is you MAC address.

This one: HWaddr 00:13:02:A0:E1:6A

That will say that you MAC address is: "00:13:02:A0:E1:6A"

Hope you get it to work, im fighting whit wifi my self... :)

---

