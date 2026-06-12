---
title: "refresh rate problem"
date: 2005-06-24
forum: Absolute Beginner Talk
---

### Post by bogdan85 on 2005-06-24
hy all
I have just installed Ubuntu. I have a question. My current resolution si 1024*768 with 60Hz refresh rate. How can I change my refresh rate to a minimum of 70 or 80 Hz? please help me. Thanks and...just for u to know it...Romania loves UBUNTU !!!!

---

### Post by frodon on 2005-06-24
This thread is really interesting for xorg configuration and settings : [http://www.ubuntuforums.org/showthread.php?t=21984&highlight=xorg](http://www.ubuntuforums.org/showthread.php?t=21984&highlight=xorg) you will find here all you need.

---

### Post by bogdan85 on 2005-06-24
Thanks but it doesn´t help me. It only changes the resolution and not the refresh rate. My current refresh rate is [COLOR=Red]60Hz[/COLOR] and it is killing my eyes. I don´t know how to change it. Anyone has a ideea? Please... Do it for my eyes  :razz:

---

### Post by frodon on 2005-06-24
lol, ok

post your xorg.conf file if you want someone to help you.
```
gedit /etc/X11/xorg.conf
```
paste here the content of your file.

1- Go on internet and have look to your screen specifications, particularily on the allowed resolutions.
2- Choose between these resolutions the one that you want.
3- Paste the result (in bold) of this command in the monitor section of your xorg.conf file :
I give you an example of the command if you want 1280*960 80Hz resolution
```
gtf 1280 960 80
# 1280x960 @ 80.00 Hz (GTF) hsync: 80.40 kHz; pclk: 140.22 MHz
**Modeline "1280x960_80.00"  140.22  1280 1376 1512 1744  960 961 964 1005  -HSync +Vsync**
```
4- If it still not work after a Xserver restart, adjust the VertRefresh parameter in monitor section of xorg.conf to 80 in this example (80Hz) or your wanted refreshrate
5- Close your eyes !!!!  :razz:

---

### Post by poofyhairguy on 2005-06-24
[QUOTE=bogdan85]Thanks but it doesn´t help me. It only changes the resolution and not the refresh rate. My current refresh rate is [COLOR=Red]60Hz[/COLOR] and it is killing my eyes. I don´t know how to change it. Anyone has a ideea? Please... Do it for my eyes  :razz:[/QUOTE]

This command will let you change it. Paste it into the terminal:

> sudo dpkg-reconfigure xserver-xorg

---

### Post by bogdan85 on 2005-06-24
Ok. Finally done it. Thanks to frodon and poofyhairguy. I managed to change what you told me. Now it looks like this :
[COLOR=Red]Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-57
	VertRefresh	[COLOR=DarkOrange]65-85[/COLOR]
EndSection[/COLOR]
Thanks again.
BTW, my eyes are ok now.   :roll:

---

