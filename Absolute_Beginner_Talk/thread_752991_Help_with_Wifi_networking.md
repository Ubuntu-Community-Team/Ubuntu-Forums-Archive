---
title: "Help with Wifi networking"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by MapHtH on 2008-04-12
Hi there

Im really really new to linux, but I can't say that I don't understand anything...
Anyway, here is the problem:

I can't seem to connect to my wireless network at my house. At first I thought that it was due to the wpa-psk encryption, but now I don't know why is it like that.
I was playing with it one whole day just to freak out and try to connect with wep or without any protection.

It gets wierd here. I couldn't connect to any router (I have two wlan routers at home) any way I tryed. But! Lol! I could connect to my neighbours router and surf without problems. 

Wired Connection works excellent.

I tryed everything, dhcp on, dhcp off, wep, wpa, wpa2... Nothing. Both of my windows desktop computers connect without problems, so it's not in the router.

I have a toshiba laptop L30-113 with Atheros ar5005g chipset. The routers are ZyXEL P-660HW-D3 and a Planex blw-04em.

Please help.
Thank you

---

### Post by stoodleysnow on 2008-04-12
Have you checked the settings the Windows machines are using?
Open or shared connection type?
Any MAC filtering?
Owt else you haven't thought of?

---

### Post by 19bab79 on 2008-04-12
it could be driver issues  with linux and those routers. do a google search for "linux drivers for <router name>"

---

### Post by bred on 2008-04-12
try this [http://ubuntuforums.org/showthread.php?t=603154]("http://ubuntuforums.org/showthread.php?t=603154")
if doesn't work could be driver issues
good luck

---

### Post by MapHtH on 2008-04-12
Hmm...

I tryed everything you guys said, but it didn't help.
I don't know why I can connect to my neighbours unprotected wlan, and no to mine.

I have found something out, though. When I log in to the router and select active wlan status, I notice that my toshiba is recognised by its MAC address, but only for 30 seconds or so. Than it disconnects from the router, but still shows that it's connected to the router in ubuntu system bar.

Would it maybe help if I disable restricted drivers and install Madwifi drivers or something?

---

