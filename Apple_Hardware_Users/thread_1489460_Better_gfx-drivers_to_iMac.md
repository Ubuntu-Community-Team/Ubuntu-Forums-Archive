---
title: "Better gfx-drivers to iMac?"
date: 2010-05-21
forum: Apple Hardware Users
---

### Post by Azyx on 2010-05-21
Hey.
I have installed Ubuntu 10.04 8Lucid lynx) on an iMac g4 800MHz 'flatscreen'. works nice, bt the grafics are little slow and ugly.

lspci gave this gfx-card:

```
0000:00:10.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go] (rev a3)
```

when i look for System-->Admin-->Hardware drivers there are nothing, not installed or proposed to install.

Is there any better gfx-driver? propretatian or not?

/Cheers

---

### Post by linuxopjemac on 2010-05-21
your best bet is nouveau (open source)

---

### Post by Azyx on 2010-05-21
> **linuxopjemac said:**
> your best bet is nouveau (open source)
 
What is the default and how do i know what driver I have? Unfortually, I'm not at home now.
 
for a couple of years ago, and even now, the propetarian driver work better for booth nvidia and ati-gfx, is my experience. Maybe on newer gfx the open alternative are better?

---

### Post by linuxopjemac on 2010-05-21
just post your /etc/X11/xorg.conf file. I have a working one for you
[here]("http://mac.linux.be/content/xorgconf-ilamp-g4-1-ghz")

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "dri2"
	Load  "extmod"
	Load  "record"
	Load  "dbe"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
	Identifier  "Card0"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "NV18 [GeForce4 MX with AGP8X (Mac)]"
	BusID       "PCI:0:16:0"
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
```

I would try to replace the driver "nv" to "nouveau", to see if that makes a difference.

---

### Post by Azyx on 2010-05-21
Thanx inuxopjemac
 
Will check this out and test when I'm coming home.
 
A little remark. I saw you have Nv18 and not Nv17 in you xorg.conf file. 
I have had bad experience of installing newer driver, that not are not supported.
 
Cheers

---

### Post by linuxopjemac on 2010-05-21
That does not matter. It's just a name. The important thing is the driver and the BusID.

---

### Post by Azyx on 2010-05-21
There are no xorg.conf in /etc/X11/. on Ubuntu 10.04 :(

May I just put one there? If something going wrong, is it just to erase it in a terminal?

Is there any other way to just check how Xserver are configurated?

---

### Post by linuxopjemac on 2010-05-21
just copy and paste, yes (as super user) If it does not work, you can always delete it

---

### Post by Azyx on 2010-05-21
It did not work :( I tried to put a xorg.conf you posted, but Ubuntu did not start...only a black screen for at least 20min.

I started a live-session and manage to mount and find and delete /etc/X11/xorg.conf, but it did not help.

I made a new install, but now with separated / and /home partition and it work now. I will read more on iLinux to see if there is a problem later on and for now use the default gfx-drivers.

/Cheers

---

