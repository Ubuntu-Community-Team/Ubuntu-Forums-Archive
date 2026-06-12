---
title: "nVidia card works great then doesn't w/ restricted drivers."
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by jmchaffie on 2007-07-29
Greetings all... I have come accross a stumper and I don't know what to do.
I installed a new 7600GT card in my computer. I went ahead and did a complete -new- fresh install of Ubuntu feisty.

Everything runs perfect. Installed the restricted drivers for the video card using the "System > Administration > Restricted Drivers..." Method... worked like a charm. Beryl and all OpenGL games ran perfect.

All of a sudden, 3 reboots later, no video. You can hear the 'beep' letting you know it's ready to login, but no video. You can even login blindly and hear the startup sound... but no video.

I can manually edit my xorg.conf file and change it back to a "vesa" card and it will work great. But the instant I try to install the restricted drivers from this point forward... same thing. No video.

Crazy thing is... Even with a fresh install it did the same thing. Worked for a while then nothing... even if I try to backup my xorg.conf first, then do the restricted drivers, then revert after the failure, then try restricted again... no video after the first failure period.

Anyone else have this problem or know of the bug? Here is my "good" xorg.conf with restricted drivers running when it is very first working right.

::::::::
Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	Busid		"PCI:5:0:0"
	
	
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

obviously the original xorg.conf is just a standard vesa driver.

THANK YOU SO MUCH for any help you can provide,
John

---

### Post by jmchaffie on 2007-07-29
Ok, well I once again tried saving my standard vesa config, then re-enabling the restricted drivers. Guess what? IT WORKED! 

Now I have a greater issue I suppose. Why is it intermittent? I am of course happuy that it is now working, but still wonder why it will just all of a sudden blink out and not work for a while, and now it's working ok.

If anyone has any information into this, please let me know.

Thanks a mint!

---

### Post by jmchaffie on 2007-07-29
Yup.. it did it again.. I just don't get it. Ok oh well I give up. This sure was the best and easiest distro I had come across so far. Really seemed like I had found the way out of windows but here I am again.

---

### Post by jmchaffie on 2007-07-29
Sorry Just saw that the original was my vesa card edit... this is the nvidia device section when the restriced drivers are enacted... if it makes any difference.

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:5:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Thanks

---

