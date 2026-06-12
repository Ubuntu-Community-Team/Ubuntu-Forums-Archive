---
title: "Newbie iBook monitor question"
date: 2005-02-23
forum: Apple PPC Users
---

### Post by playahater on 2005-02-23
I have iBook with 500Mhz cpu and 256Mb memory .. 
I have installed unbuntu and I want to make xf86config but I don`t know what to put in monitor section .. 
vertical and horizontal refresh rate ???

Any help ??  [-o< 
and btw do I need to install ati rage 128 driver in order to enable 3d acceleration or not .. I want to play Q3  ;-) 

Greetings   :)

---

### Post by tgomas on 2005-02-25
[QUOTE=playahater]I have iBook with 500Mhz cpu and 256Mb memory .. 
I have installed unbuntu and I want to make xf86config but I don`t know what to put in monitor section .. 
vertical and horizontal refresh rate ???
[/QUOTE]

on my ibook 500Mhz dual usb I have:

Section "Monitor"
	Identifier	"lcd"
	HorizSync	28-49
	VertRefresh	43-72
	Option		"DPMS"
EndSection

---

### Post by playahater on 2005-02-25
Woww .. thanx man .. 
Its working .. i`ve even enabled 3d acceleration .. 

Thanx ..

---

