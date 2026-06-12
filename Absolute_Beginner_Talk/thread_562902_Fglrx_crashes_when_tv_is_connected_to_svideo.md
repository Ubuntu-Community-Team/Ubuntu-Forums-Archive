---
title: "Fglrx crashes when tv is connected to svideo"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by mikeserv on 2007-09-29
I pump video out to my TV a lot, so I have my TV connected to the S-Video out port on the back of my video card (an ATI X1300).  But every time I try to boot into Linux with the TV connected I get an error message "No Device for PCI BusID 1:0:1" and X refuses to load.

Here's my xorg.conf:

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "DELL 2007WFP" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "DELL 2007WFP"
	HorizSync    30.0 - 83.0
	VertRefresh  56.0 - 76.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "DELL 2007WFP"
	Device     "Generic Video Card"
	Monitor    "DELL 2007WFP"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050_60.00" "1280x1024" "1152x864" "1024x7685" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

---

### Post by mikeserv on 2007-09-29
Any suggestions?

---

### Post by michael37 on 2007-09-29
Disconnect TV and connect the regular monitor.

Back up your xorg.conf

Use aticonfig utility to configure your computer with monitor and TV (you may need to download it, I think the sudo apt-get install aticonfig should do it, I may be a bit off though).

aticonfig changes your xorg.conf, so you will need to restart X before connecting  TV.

---

### Post by mikeserv on 2007-09-29
I have aticonfig.  But how exactly do I use it to "configure computer with monitor and tv?"

-Mike

---

### Post by michael37 on 2007-09-29
> **mikeserv said:**
> I have aticonfig.  But how exactly do I use it to "configure computer with monitor and tv?"

-Mike

Best way: run 
```

aticonfig -h

```
and read the instructions

Not a good way: listen to me who has never set up TV since I don't need it.  Btw, my video card is X1400 in a laptop.  From aticonfig -h:

```

Setting up fglrx for the first time.
       Single head :    aticonfig --initial --input=/etc/X11/xorg.conf
       Dual head   :    aticonfig --initial=dual-head --screen-layout=above
                        This command will generate a dual head configuration
                        file with the second screen located above the first
                        screen.
Force primary CRT on and TV-out on.
                        aticonfig --force-monitor=crt1,tv

```

As I said, before experimenting with aticonfig, backup your xorg.conf and restore it in case aticonfig screws your computer.

---

