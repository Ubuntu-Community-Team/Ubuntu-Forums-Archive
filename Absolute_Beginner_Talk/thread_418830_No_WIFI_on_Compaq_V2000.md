---
title: "No WIFI on Compaq V2000"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by CronoBuntu on 2007-04-22
Hi,

I succesfully installed Ubuntu as a Dual-Boot with Win XP, but when i first started, i couldnt make wifi start working even when i tried a lot of stuff and followed a lot of guides. I spent lots of hours and nothing. I dunno if somebody can explain me how to do it from the start. 

My laptop is a Compaq Presario V2570NR (V2000 series) with broadcom WiFi adapter. Ubuntu has my wifi identified at "eth1". I hope somebody can help, im new at linux, just started using it like 5 days ago, but i read a lot these days. Thanks a lot. :)

---

### Post by altaaa on 2007-04-22
- Which ubuntu version are you using?
- Is your wireless LED on your laptop turned on?
- If you go to System > Administration > Network, and configure the wireless interface manually, does it work?
- Do you use NetworkManager?

---

### Post by CronoBuntu on 2007-04-22
1. I installed 7.04 Final
2. At the start i have it off, but after some code i used on terminal i made it turn on. i installed bcm package too.
3. I cannot configure it manually, cuz i dont have the option for a WPA password there, just WEP :confused: and even when i did it, it doesnt work.
4. And yes i used network manager.

With terminal, i scaned wifi nearby and i got connected to my wifi, i have the signal at 70% and all, but still doesnt work (i mean the browser shows like no connection at all). When i select connection info, address, gateway and all is set to "0.0.0.0" and i cannot change it.

---

### Post by altaaa on 2007-04-22
Which bcm package did you install?

This worked for me:

```
wget http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb

dpkg -i ./bcm43xx-firmware_1.3-1ubuntu2_all.deb
```



Network Manager should support WPA out-of-the-box.

---

### Post by CronoBuntu on 2007-04-22
Yeah, i installed that one.

And im sure, i only have 2 options, and both are WEP.
I have 3 choices at network manager, first one, Wifi, second LAN and third modem. at the wifi configuration i can only see WEP.

---

### Post by altaaa on 2007-04-22
Is it possible you are referring to the Network Settings window? That is not the way Network Manager works, you have a Network Manager icon next to your clock, if you click on that with your left mouse buttons you should be able to select all wireless networks within range. 

I can connect to virtually every wireless network, WEP, WPA, or non encrypted. In the Network Settings window, however, I also only can choose between two WEP options. Do you have checked the Roaming option?

---

### Post by rtprice on 2008-02-24
> **altaaa said:**
> Is it possible you are referring to the Network Settings window? That is not the way Network Manager works, you have a Network Manager icon next to your clock, if you click on that with your left mouse buttons you should be able to select all wireless networks within range. 

I can connect to virtually every wireless network, WEP, WPA, or non encrypted. In the Network Settings window, however, I also only can choose between two WEP options. Do you have checked the Roaming option?
    i dont have this icon any more and i can not figure out where it went.i also cant use wireless.any ideas?same type LT

---

