---
title: "no connection"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by next on 2005-06-21
ok i just installed the drivers for my d-link dwl-g510, i went to networking configured device, then activated it.  i tried to open up firefox and i still didn't have a connection. 



PS:  for the ip addres, subnet mask ect. i used the numbers my psp was using to connect to the internet.  is that ok??




am i missing a step or what am i doing wrong?

---

### Post by poofyhairguy on 2005-06-22
[QUOTE=next]ok i just installed the drivers for my d-link dwl-g510, i went to networking configured device, then activated it.  i tried to open up firefox and i still didn't have a connection. 
[/QUOTE]

Well....let me tell you about a little bug in Ubuntu. That network tool will say that a connection is active when its not. My rule of thumb is if it takes more than 20 or so secs to connect, its not working.

What have you done so far? What access point are you trying to connect to?

---

### Post by next on 2005-06-22
i  turned on my computer today and the card didn't even show up on network settings. i had to "sudo modprobe ndiswrapper" first.

---

### Post by somuchfortheafter on 2005-06-22
once network whatever says it is active
open a terminal and type ifconfig and post what it has there...

---

### Post by next on 2005-06-22
[QUOTE=somuchfortheafter]once network whatever says it is active
open a terminal and type ifconfig and post what it has there...[/QUOTE]
 lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1561 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1561 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:138668 (135.4 KiB)  TX bytes:138668 (135.4 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:3D:51:B9:35
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:3dff:fe51:b935/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:191 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:56969 (55.6 KiB)  TX bytes:7518 (7.3 KiB)
          Interrupt:18 Memory:40100000-4010ffff

---

### Post by next on 2005-06-22
[QUOTE=somuchfortheafter]once network whatever says it is active
open a terminal and type ifconfig and post what it has there...[/QUOTE]
 cant people hack my computer if i give my ip address and stuff?   i dunno

---

### Post by next on 2005-06-22
can i give you just a specific part??

please help me out i dont want to go back to windows :-|

---

### Post by IchBin on 2005-06-24
[QUOTE=next]can i give you just a specific part??

please help me out i dont want to go back to windows :-|[/QUOTE]
 If you're real ip is in there just put x's in place of it. Post your output so everyone can see if they can help.

---

### Post by next on 2005-06-25
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1586 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:140869 (137.5 KiB)  TX bytes:140869 (137.5 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:3D:51:B9:35
          inet addr:XXXXXXXXX Bcast:XXXXXXXXX Mask:XXXXXXXXXX
          inet6 addr: fe80::20f:3dff:fe51:b935/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:197 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:64745 (63.2 KiB)  TX bytes:378 (378.0 b)
          Interrupt:18 Memory:40100000-4010ffff

---

### Post by jasmuz on 2005-10-04
NeXt, your Wireless is recognized.

You just need to configure an IP for it via iwconfig.

---

