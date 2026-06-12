---
title: "Someone Help - SyncCE /WM5"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by wperdomos on 2006-12-27
Hi, The guys of syncce post a method to connect WM5 Devices to SyncCE using USB and usb-rndis-lite driver.

[http://www.synce.org/index.php/Windows_Mobile_2005_Support]("http://www.synce.org/index.php/Windows_Mobile_2005_Support")

Can Please someone do a "NooB Style how to" to do this?

Doesnt look complicated but im having a lot of erros compiling SyncCe and drivers.
Ive managed to install Cedega ati drivers and run games like GW WOW w that, but this is anoying, got a couple of days on this w no luck.](*,) 

Hope someone can take some mins to do a mini faq about this.

Ubuntu Dapper and Qtek WM5.

Thanks a lot.

---

### Post by edmondt on 2007-01-22
Bump! I would like to get this working too...

When I connect my device I can see:

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=ef(unk. ) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0bb4 ProdID=0bce Rev= 0.00
S:  Manufacturer=HTC
S:  Product=Generic RNDIS
C:* #Ifs= 2 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=ef(unk. ) Sub=01 Prot=01 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=1ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=03(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

But I can't find my device on dmesg, I don't have ttyUSB0 on dev... Can someone post a good how to on this? it would be a major step forward for many ubuntu users to sync their WM5 device with Evolution :)

---

### Post by edmondt on 2007-01-30
I've learned how and I've got a how to just so that others can do it too:

[http://www.ubuntuforums.org/showthread.php?t=345176&highlight=WM5](http://www.ubuntuforums.org/showthread.php?t=345176&highlight=WM5)

---

