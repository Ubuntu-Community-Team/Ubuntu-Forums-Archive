---
title: "No  GUI in ubuntu/xubuntu xorg.conf problem"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by normwheatley on 2007-06-29
Hi,

I'm new to all this but I do have some Unix experience. I have a Dell LAtitude CPI 400 laptop.
I installed ubuntu server (annihilating XP). It went smoothly but not GUI interface - not that I was expecting one (oh, LAMP didn't go well either but that's another story).
I want to be able to use a web browser, MySQL Server GUI etc so I installed gdm, then tried xterm and nothing happened (although I did get apache going before and after I installed MySQL Server).

 So I installed Xubuntu Desktop over the ubuntu server. Again no real problems but still nothing GUI going on.
I'm not sure but I think that the GUI interface on ubuntu is xterm and you need xserver properly installed with gdm running and DISPLAY set, is this correct?

So, I tried running xterm, this failed. I tried installing xserver (sudo apt-get install xserver-xorg-core) it seemed to go ok except that it still no gui and I got an error complaining about my xorg.conf - the log says 
(WW) the directory"/usr/share/fonts/X11/misc" does not exist ... there are a few more of these then down the bottom it says ...
(EE) AIGLX: Screen is 0 not DRI compatible
(EE) xf860penSerial: cannot open device /dev/input/wacom ... tries this a few times then ..
Could not init font path element /usr/share/fonts/X11/misc, removing from list ... a bunch of these, corresponding to all the warmings (10 of them) it gave at the start of the log

So, any ideas what could be astray? 

here's part of the xorg.conf

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "DRI"
	Mode	0666
EndSection

thanks

Norm

---

### Post by tarek on 2007-06-29
Did you use this command to install xubuntu: sudo aptitude install xubuntu-desktop?

---

### Post by avik on 2007-06-29
Can you post the Modules section of your xorg.conf?

---

### Post by normwheatley on 2007-06-29
Hi,

After the ubuntu install I then burnt xubuntu to CD and installed that. I can't recall if I later did a 
sudo aptitude install xubuntu-desktop although I might've seeing as the GUI still didn't work.

I did examine my xorg.conf and saw that it got the video driver wrong so I ran sudo dpkg-reconfigure xorg and
put in the neomagic2360 which appeared in the xorg log file ok. However it still fails.

So, here's the current xorg.conf with the Xorg.0.log file as an attachment

thanks
Norm

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Cardneomagic2360"
	Driver		"neomagic"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitorneomagic2360"
	Option		"DPMS"
	HorizSync	28-33
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Cardneomagic2360"
	Monitor		"Generic Monitorneomagic2360"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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
EndSection

--------------------------------

The Xorg.0.log file is an attachment

---

### Post by tarek on 2007-06-29
Can you run sudo dpkg-reconfigure xorg again and go with the default options this time.

---

### Post by normwheatley on 2007-06-29
I did that already (ran it several times). It's kinda hard as there are so many questions and the "default" is never obvious. Do you have anything specific in mind?
ta
Norm

---

### Post by tarek on 2007-06-29
The default driver is vesa - I think. I had some problems with my xorg.conf and I just ran that command and went with the default options, it worked.

After that I installed the right video card driver. Do you have an ATI card?

---

### Post by normwheatley on 2007-06-29
Hi,

"vesa" was the original driver that it chose ... and that didn't work.
Where does the Video device name eg neomagic2360 come in?

ta
Norm

---

### Post by tarek on 2007-06-29
I don't know why it's not working.

Do you have an ATI card?

---

### Post by normwheatley on 2007-07-02
Hmmm. I'm not sure, it doesn't say anything in the setup (other than the neomagic 2360).
It's a Dell Latitude Cpi R400GT laptop, does that help?

thanks
Norm

---

### Post by Raineer on 2007-07-02
Very strange, as Vesa will work for just about anything.

I don't know if I'm alone, but Xorg.0.conf doesn't show as an attachment to me. Can you try again or post like the last 20 lines of it?

By the way, didn't see anyone mention it. Those font errors you see are practically normal, they will **not** keep you from booting X so don't worry about that. The Driver "neomagic" line is what we're mostly looking at, that is likely where it's failing.

---

### Post by normwheatley on 2007-07-02
Hi,

I got it working. I had to re-install (ie sudo apt-get install xorg) and it now works great!

thanks very much for  your help!

Norm

---

