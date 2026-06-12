---
title: "MacBook 2,1 eth0 dead"
date: 2011-04-24
forum: Apple Hardware Users
---

### Post by Geremia on 2011-04-24
Every ethernet wire I have recently used does not activate the connected light on the router to which I connect my MacBook 2,1. It has worked under both Ubuntu and Mac OS X. Here is the output of some commads:

[FONT=Courier New]ifconfig eth0[/FONT]:```
eth0      Link encap:Ethernet  direcciónHW 00:17:f2:31:d3:74  
          ACTIVO DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
          Interrupt:16
```Output of lscpi pertaining to ethernet card:```
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
```Results of some other commands:```
$ sudo ifdown eth0
Ignoring unknown interface eth0=eth0.
``````
$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.
``````
sudo ifconfig eth0 up
```does not return anything, nor does it with "down" instead of "up." My wireless (wlan0) works just fine. What is going on with eth0, and why have I had this problem just recently? Wired says "disconnected" in the NetworkManager 0.8.1.
Thanks

---

