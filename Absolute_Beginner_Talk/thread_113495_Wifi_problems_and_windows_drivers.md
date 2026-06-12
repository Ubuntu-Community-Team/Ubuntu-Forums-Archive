---
title: "Wifi problems and windows drivers"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by Zapol on 2006-01-06
Hi, first of all I just want to say how fantastic ubuntu is. I downloaded it today and just love it. A million congratulations to everyone involved!

My only problem is getting it (on my laptop) to recognise my wireless card. I have the windows drivers on CD but can't work out how to get them onto ubuntu properly. The ethernet works without problem. I searched the forums under "import windows drivers" but nothing relevant turned up (I think).

I'd be very very grateful for any help or advice you guys could offer me. Thanks in advance, and I apologise if this is a stupid noob question! :D

---

### Post by bluefrog on 2006-01-06
sudo apt-get install ndiswrapper  (on the cd)
put your windows (driver.inf and driver.sys) in a folder

sudo ndiswrapper -i /path/to/folder/driver.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper

u should see your card in system>administration>network.
configure and activate.

james

---

### Post by manofsteel on 2006-01-06
you have to enable the wifi in the control panel, its disabled if you connected through a lan line during install. I'm not infront of my Ubuntu desktop right now and i cant remember how to get where you need to get but check the menues for network configs or somthing like that. then you'll see both ur ethernet port and the wifi just highlight it by clicking on it then click on enable.

---

