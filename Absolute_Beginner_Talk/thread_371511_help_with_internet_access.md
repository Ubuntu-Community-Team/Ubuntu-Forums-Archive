---
title: "help with internet access"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by qred on 2007-02-27
I am having problems connecting to the internet with the ubuntu live cd.  I have a verizon wireless v640 express card (hope that helps).   

Any help would be greatly appreciated as I have searched for a solution, yet still haven't found one.  This is all very new to me so any answers would be great.

thanks

---

### Post by SqRt7744 on 2007-02-27
the card that you have... does it use UMTS?  That is, is a PC card in your computer that connects to the internet through the cell network, or does it connect over WiFi with your router?

Open a termnial and copy the output of lspci into a reply.

Also the output of ifconfig would be nice.  Thanks!

---

### Post by qred on 2007-02-28
I appreciate the reply, however am afraid I am in over my head.  Honestly, I am not really sure what you just asked from me or how to access that information.

---

### Post by antdedyet on 2007-06-09
The Verizon Wireless V640 didn't show up under lspci or lsusb in Feisty, but I found some information about it in /proc/bus/usb/devices:

```


T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1410 ProdID=1100 Rev= 0.00
S:  Manufacturer=Novatel Wireless Inc.
S:  Product=Novatel Wireless EXPD CDMA
C:* #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=airprime
E:  Ad=81(I) Atr=03(Int.) MxPS=  64 Ivl=128ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=airprime
E:  Ad=84(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=04(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms


```

It shows up in ifconfig/iwconfig as eth1 in roaming mode by default while using the LiveCD. Since MAC addresses are unique, second half has been replaced in this post.

```


eth1      Link encap:Ethernet  HWaddr 00:18:DE:XX:XX:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:2562 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0x4000 Memory:90200000-90200fff


```


I'd like to get this card working for my Acer TravelMate 8210. 

In Windows XP, the device uses some software to dial a specific access number (#NNN) and then the unique authentication credentials seem built-in to the cards firmware (I didn't see it listed anywhere in the software configuration).

---

