---
title: "Fast xorg.conf for 12 inch iBook G4"
date: 2005-09-23
forum: Apple PPC Users
---

### Post by stuporglue on 2005-09-23
I saw that someone with Fedora Core 4 had gotten ~1700 fps on a 12 inch iBook G4, but I was only getting arround 600 or so, so I set out to find a better xorg.conf. 

I found I could only get those speeds if I didn't use an external monitor, which was fine with me. I couldn't find a fast xorg.conf on these forums, so I'm posting mine here.

lspci says my video card is a "VGA compatible controller: ATI Technologies Inc RV250 5c63 [Radeon Mobility 9200 M9+] (rev 01)"

I didn't get this xorg.conf from this page, but it does have some good confs for making the external monitor work in either spanning or mirrored modes 
[http://www.aronchi.org/LinuxOnIBookG4](http://www.aronchi.org/LinuxOnIBookG4)

Here's the xorg.conf

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
#	Option  "BlankTime"  "5"  # Blank the screen after 5 minute (Fake)
	Option  "StandbyTime"  "10"  # Turn off screen after 10 minutes (DPMS)
#	Option  "SuspendTime"  "20"  # Full suspend after 20 minutes
	Option  "OffTime"  "15"  # Turn off after half an hour
	
EndSection

Section "Files"
	RgbPath      "/usr/X11R6/lib/X11/rgb"
	ModulePath   "/usr/X11R6/lib/modules"
	FontPath     "/usr/share/fonts/misc/"
	FontPath     "/usr/share/fonts/TTF/"
	FontPath     "/usr/share/fonts/Speedo/"
	FontPath     "/usr/share/fonts/Type1/"
	FontPath     "/usr/share/fonts/75dpi/"
	FontPath     "/usr/share/fonts/100dpi/"
EndSection

Section "Module"
	Load  "record"
	Load  "extmod"
	Load  "dbe"
	Load  "dri"
	Load  "glx"
	Load  "xtrap"
	Load  "freetype"
	Load  "type1"
	Load  "speedo"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "keyboard"
	Option	    "XkbOptions" "lv3:lwin_switch"
	Option      "XkbModel" "pc105"
	Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option      "ZAxisMapping" "4 5" 
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	Option	"DPMS"	"true"
EndSection

Section "Device"
	Identifier  "card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon 9200 Mobility"
	BusID       "PCI:0:16:0"
	Option      "UseFBDev"
	Option      "AGPMode" "4"
	Option      "EnablePageFlip" "On"
	Option "backingstore" "true" #added for xcompmgr
	Option "RenderAccel" "true" #added for xcompmgr
EndSection

Section "Device"
	Identifier "radeon-clone"
	Driver	"radeon"
	Option "DDCMode" "true"
	Option "CloneMode" "1024x768"
	Option "CRT2HSync" "31.5-80"
	Option "CRT2VRefresh" "56.3-75"
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option "Composite" "Enable"
	Option "RENDER" "true" #added for xcompmgr
	Option "DAMAGE" "true" #added for xcompmgr
EndSection
```

---

### Post by refdoc on 2005-09-26
Thanks, will try this out

---

### Post by Arne Caspari on 2005-09-29
I tried it gives an acceleration ( from about 600 to ~920 on my iBook G4 800). With Breezy, remember you have to run glxgears with: 
```
glxgears -iacknowledgethatthistoolisnotabenchmark
```(stupid!:-/)
The configuration above enables composite, render and damage extensions but if I acutally use them with xcompmgr, OpenGL apps have display errors ( The windows flicker or get entirely black ).

---

### Post by stuporglue on 2005-09-29
> The configuration above enables composite, render and damage extensions but if I acutally use them with xcompmgr, OpenGL apps have display errors ( The windows flicker or get entirely black

Oh yeah, sorry about that. 

I tried it without using xcompmgr and didn't notice anything bad happen for a day or so, then I forgout about those lines. I think if you leave them, they won't do anything, unless you run xcompmgr, but someone smarter can probably correct me.

---

