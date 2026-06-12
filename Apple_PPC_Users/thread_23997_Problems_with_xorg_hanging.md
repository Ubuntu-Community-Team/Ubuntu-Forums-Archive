---
title: "Problems with xorg hanging"
date: 2005-04-04
forum: Apple PPC Users
---

### Post by keifer on 2005-04-04
Ok, I have a rather annoying, but not too bad problem, with xorg.

I can run xorg normaly, untill I need to kill the server (shutdown, reboot, supsend, exit to cli, etc). When I kill xorg, I get stuck with a red screen untill the computer is shutdown. It dosent seem to be hanging the computer, because when I shutdown, or reboot the system via gdm, I just see the red screen untill the shutdown processes are finished, and then the computer powers down.

Like I said, it's not a problem that is ground breaking, but it is annoying, and keeps me from using the suspend function (which would be nice to have).

_______

[my hardware: 2002 lcd imac, 800 mhz, gforce2 MX]

my xorg.conf:

```
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nv"
	BusID		"PCI:0:16:0"
EndSection

Section "Monitor"
	Identifier	"Color LCD"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"Color LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by crane on 2005-04-05
One thing you might try is installing nvidia driver. Should be able to find plenty of info on the forums.
I think it's 
sudo apt- get install nvidia-glx
sudo nvidia-glx-config enable
restart X

---

### Post by keifer on 2005-04-05
[QUOTE=crane]One thing you might try is installing nvidia driver. Should be able to find plenty of info on the forums.
I think it's 
sudo apt- get install nvidia-glx
sudo nvidia-glx-config enable
restart X[/QUOTE]
 I checked the package list in synaptic, and all I found that looked close was "nvidia-kernel-common". Unfortanatly, it doesn't look like that was it. Is there a specific repository I need to enable?

---

### Post by lordmule on 2006-07-10
Weird, i thought the local mirrors would have nvidia-glx. Have you tried enabling the universe/multiverse via /etc/apt/sources.lst ?
If that wouldnt work try adding a different mirror.

I recently got frustrated with dappers xorg and went back to breezy.

---

