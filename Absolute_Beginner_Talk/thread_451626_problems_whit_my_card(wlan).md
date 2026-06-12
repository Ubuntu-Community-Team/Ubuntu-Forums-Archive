---
title: "problems whit my card(wlan)"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Explode2 on 2007-05-22
Hi everyone , I got some problems with my Netgear WG511U card..whenever I try to set it to monitor mode with the command :
sudo iwconfig ath0 mode monitor
some error appears and tells me :
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.
any suggestions what I am doing wrong?

regards Explode2

---

### Post by weatherman1293 on 2007-05-22
Does the GUI act as if there is a card installed?

---

### Post by Explode2 on 2007-05-22
Yes it acts like a card driver and stuff like that is installed, one time I tried this under live cd  (ubuntu feisty 7.04) and than It worked, now I nstalled the system on my harddisk and its working now not.... :(
When I am doing a ifconfig, it tells me than :
from my card the 2 adresse:

ath0      Protokoll:Ethernet  Hardware Adresse xx:xx:xx:xx:xx:xx 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Protokoll:UNSPEC  Hardware Adresse 00-0F-B4-34-3D-44-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:199 
          RX bytes:836 (836.0 b)  TX bytes:2944 (2.8 KiB)
          Interrupt:11

---

