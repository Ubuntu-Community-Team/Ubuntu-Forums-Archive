---
title: "eth0 configured w/ XP ipconf settings failed"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by supervisor on 2006-08-07
Hello,

I would like to connect a Motorola Surfboard 5100 cable modem to my Gateway M460 notebook w/ Ubuntu Ver 5.10. Here is my last forum search; "[http://www.ubuntuforums.org/search.php?searchid=7276382]("http://www.ubuntuforums.org/search.php?searchid=7276382")"

Manual configuration of Ubuntu network settings using "ipconfig" in XP "cmd" window was unsuccessful
Have completely read "[InternetHowTo]("https://help.ubuntu.com/community/ADSLPPPoE")" was not helpful in creating successful connection. "sudo pppoeconf" command in terminal caused "Sorry..." error message.

This post is being generated via a PC AMD Sempron 3800+ 64 bit system running Win XP Pro SP2. I have no way to copy the error logs from my notebook to this PC. My u;timate goal is for my notebook to connect with high speed wireless and play DVDs when not running office programs. Any assistance is appreciated.

Thank you in advance.

---

### Post by rdd on 2006-08-07
When you used pppoeconf, what happened? Could you describe yuor setup (Modem directly hooked up to the notebook via ethernet?)?
Just some more details please.

Regards

rdd

---

### Post by supervisor on 2006-08-07
Rdd,

Thank you for such a rapid response. I am not able to fully transcribe the error log ["dmesg"] but "sudo pppoeconf" did go through the multi scanning sequence and recognized my regular and ethernet modems. [ethernet=eth0, wireless=eth1"]


Have read "[https://help.ubuntu.com/community/ADSLPPPoE]("https://help.ubuntu.com/community/ADSLPPPoE")" Based on the reccomendations, I have installed the USB Cable Modem drivers for my PC so that my notebook can use the ethernet cable to the modem. I have read the forum rules and guides and will post as much information regarding the problem whenever possible.

Regards,
Joshua

---

### Post by rdd on 2006-08-07
Hi Joshua, 

first you have to decide. As I understand your modem has both an ethernet and a USB-Port. You can use either of them. I would, however recommend using the ethernet port as it is (I believe) better supported. 

When you connect the modem via Ethernet cable to your wired network port (I assume eth0) you should select that port in pppoeconf. Does anything happen when you do that (maybe the lights on your modem show something)?

Regards

rdd

---

### Post by supervisor on 2006-08-09
I apologize for my belated reply, work is demanding.

I troubleshot a successful solution; disable WINXP conn, disconnect USB/PC from modem, unplug modem,

wait...

deactivate eth0, connect ETH/Laptop cable to modem, plug in modem, wait for ready lights, activate eth0. Reverse directions to reconnect PC.

My ISP uses an "always on" connection [NOT asdl/pppoe] and this has worked everytime. I tested the eth0 by upgrading the notebook to Dapper Drake and installing Totem-xine for DVD playback. Thank you RDD and everyone else who replies to requests for help. I will build a router soon, this works for now.

---

