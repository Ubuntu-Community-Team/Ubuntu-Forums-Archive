---
title: "Refresh Rate"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by CosmicFlux on 2007-11-23
Hi,

I can't seem to get my screen to refresh at 75hz when using 1200 x 800 resolution. I initially was getting a maximum of 60hz in every available resolution. I installed 915resolution using Synaptic and was able to get 1200 x 800, which is my laptops screen size. I edited the xorg.conf file and upped the refresh rate to 75hz but its only working with the other resolutions and not the 1200 x 800 one. Any suggestions?

CosmicFlux

---

### Post by erginemr on 2007-11-23
Hello,

Could you please post your xorg.conf file here?

---

### Post by laidback on 2007-11-23
I believe that I read that the reported/set refresh rates are not necessarily accurate. My Acer should go to 75hz but I only get 50-55hz in Ubuntu. Sorry but I don't have a record of the POST on this one. You'll have to search for it I'm afraid. But as my screen is lovely I have given up worrying.

---

### Post by erginemr on 2007-11-24
> **laidback said:**
> I believe that I read that the reported/set refresh rates are not necessarily accurate. My Acer should go to 75hz but I only get 50-55hz in Ubuntu. Sorry but I don't have a record of the POST on this one. You'll have to search for it I'm afraid. But as my screen is lovely I have given up worrying.

No no, what I mean by "post" is if you can list what is inside your xorg.file here. You can do that by first listing your xorg.file with first writing the following commnad from the console:

gedit /etc/X11/xorg.conf

and copying all and pasting it here into your reply. 

Take Care.

---

### Post by CosmicFlux on 2007-11-24
OK, the relevant sections of my xorg.conf file is:
[B]
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-95
	VertRefresh	43-95
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection[/B]

50 - 55hz is really bad. The minimum recommended refresh rate ANY PC should be using is 75hz. Anything lower will give you headaches, eye strain etc.

---

### Post by CatKiller on 2007-11-24
> **CosmicFlux said:**
> 50 - 55hz is really bad.

50-55 isn't accurate - that's the point. If you're using Compiz then the refresh rate gets reported in the low 50s, even when the refresh rate is actually higher.

It's possible that your monitor can't do 75Hz at 1280x800. Many monitors can't do their highest refresh rates at their highest resolution.

Also, those HorizSync and VertRefresh numbers are something that you've made up, aren't they? If you put in the actual numbers from your actual monitor, you might have more luck.

---

### Post by erginemr on 2007-11-24
Normally, mode lines should look like:
Depth 24
Modes "1280x800" "1280x768" "1024x768" "800x600" "640x480"

and you stipulate refresh rates with:
Modes "1280x800@75" "1280x768@75" "1024x768@75" "800x600@75" "640x480@75"
or
Modes "1280x800_75" "1280x768_75" "1024x768_75" "800x600_75" "640x480_75"
depending upon whichever works. However, looking at your first post, I assume you already know and tried it to no avail. 

Then, the next thing to attack, IMHO, is the lines
HorizSync 28-95
VertRefresh 43-95 

You should check the manual / pamphlet for your Acer Monitor or Google it to learn and apply the horizontal and vertical refresh rates it supports.

---

### Post by chrismine on 2007-11-24
If it is a laptop it will have a LCD screen and using a refresh rate higher tha 60Hz may damage the screen - just in case you have not thought about that.

---

### Post by CatKiller on 2007-11-24
If it's a laptop then "refresh rate" is meaningless anyway. LCD cells will change when they get round to changing, pixel by pixel, unlike CRTs which have a vertical sweep dependent on how fast the electron gun can move.

---

### Post by CosmicFlux on 2007-11-24
Well, 1280 x 800 had a refresh rate of 75hz in Windows Vista...which is why I know the hardware can handle it. Also, my hardware allows a maximum of 85hz so 75hz should be OK no?

---

