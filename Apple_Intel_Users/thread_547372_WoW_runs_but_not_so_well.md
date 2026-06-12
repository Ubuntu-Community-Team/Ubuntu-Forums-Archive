---
title: "WoW runs but not so well"
date: 2007-09-09
forum: Apple Intel Users
---

### Post by kysiragi on 2007-09-09
I followed the guide to installing WoW, worked fine, followed the guide to configuring the driver and openGL, worked fine. WoW runs pretty fast, not as fast as I'd like but just one major thing to turning me away from it. When running around random things in the enviroment will just go white. A lamp at a certain angle becomes visible but once you move the camera at all, turns white. Sometimes after logging in my character is white unless i zoom in real close. So obviously its something with the 3-D rendering, any suggestions or a guide i missed? thanks in advance

---

### Post by moynihan on 2007-09-11
Are you running on a macbook or a macbook pro? If you're on macbook you can assign extra Ram to  your video card (up to 224MB) which has dramaically improve your gaming experience (personally I can run steam games within compz-fusion). Are you running your WoW with Wine, Crossover or Cedega? Also could I have a gander at your xoeg.conf?

---

### Post by kysiragi on 2007-09-12
i have a macbook C2D 2.0ghz
what command is it to assign a higher video ram value?
wine
sure:


Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "v4l"
        Load    "vbe"
        Load    "i2c"
EndSection

Section "DRI"
	Mode 0666
EndSection

---

### Post by moynihan on 2007-09-14
Take a backup of your xorg configuration.

Afterwards open your xorg.conf file and add the highlighted line to the device section.



Section "Device"
Identifier "Generic Video Card"
Driver "i810"
BusID "PCI:0:2:0"
Option "XAANoOffscreenPixmaps"
***[COLOR="Red"]Option 	"VideoRam" "65536"[/COLOR]***
EndSection

The videoram option is measured in bytes and the maximum should be 224MB. The above is 64MB 64*1024. Any value in between should work. This will take over system ram so I'd reckon you should try a few different values untill you come up with a happy medium between video and system ram. Hope this helps. Let me know how you get on.

---

### Post by kysiragi on 2007-09-14
yeah that made it work a little better but one major thing is bothering me, if you play the game yourself you might know what i mean. when i first log in, everything looks fine but once i start to go into certain areas. everyones character including mine goes white, comepletely white at every angle. and randomly the detail will come and go. same thing happens to enemy units and small things like lamps, tables, other NPC's... explain that... im baffled...

---

### Post by moynihan on 2007-09-21
I don't actually play the game myself so I m,ay not be able to help you any further. The only thing I can suggest is check out the options menu and see if you can set rendering to openGL instead. (I'm pretty sure there's a thread on the forums on how to run WoW in openGL mode but for the life of me I can't find it right now). At this stage I'd just look through the general WoW under wine threads because I think we've covered anything that's macbook specific. Hope this helps.....

---

