---
title: "Wireless disabled at startup"
date: 2011-08-05
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Arbales on 2011-08-05
Hello, im having a trouble getting working wireless on my ASUS F5SL laptop.
I'm using Ubuntu 11.04, after i turn on laptop all networks are disconnected and wireless disabled it doesn't show any connectable networks.
Wireless card Atheros AR5001.
If i try to turn off or restart network, wireless card disables fully it doesnt show on command** ifconfig** (wireless disabled by hardware switch)
I tried **ifconfig wlan0 up** but then i get **siocsifflags operation not possible due to rf-kill.**

**rfkill list**
0: phy0: Wireless LAN     
Soft blocked: no     
Hard blocked: yes

Tried **rfkill unblock all** and nothing happened hard blocked remained the same.
I tried reseting BIOS to defaults but that didn't help I even tried if wireless works in UBUNTU 11.04 live cd booted from usb it also didn't work.
If i try restarting laptop i still get [B]wireless disabled by hardware switch
[/B]Only when i shutdown and turn on laptopi get my wireless card appearin **ifconfig **but when i try to mess around with it goes [B]wireless disabled by hardware switch.
[/B]It did work beforebut after i was messing aroundwith aircrack-ng program, after shutdown wireless didnt work..
I really hope you guys can help me.

---

### Post by Arbales on 2011-08-05
Im sorry guys i am an idiot, when i was putting laptop in bag i accidentally moved button on side and switched off wireless.....
Everything works fine now.

---

### Post by THOMAS0 on 2011-08-11
The success of the series has inspired short videos for mobile phones, several official tie-ins in print and on the Internet, as well as a video game.

---

