---
title: "Dual monitors, DVI and VGA"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by Tobbz on 2006-05-24
Hi All.

I am about to give up. ](*,) 

I'm trying to get my ATI Radeon 9000 Pro to work with my 17" Xerox TFT Screen (DVI port), and my 32" Samsung LCD TV (VGA port)


Here is my xorg.conf:
```

Section "ServerLayout"
        Identifier     "Multihead layout"
        Screen      0  "Screen0" LeftOf "Screen1"
        Screen      1  "Screen1" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
        Option         "Xinerama" "off"
        Option         "Clone" "on"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
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
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "dk"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Xerox XL-775"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Samsung"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Monitor    "Xerox XL-775"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "ATI Graphics Adapter 0"
	Monitor    "Samsung"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1366x768"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1366x768"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1366x768"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1366x768"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1366x768"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1366x768"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

I have my 17" Xerox working fine. Resolution is 1280x1024.
But i can't get a signal to my 32" LCD TV. The resolution HAS to be 1366x768.
Any pointers?

Bear in mind that I've just started using Linux yesterday.

TIA

Best Regards, Tobbz

---

### Post by Tobbz on 2006-05-24
bump, anyone?

---

### Post by halfvolle melk on 2006-05-24
I came across this thread, maybe you can use it.
[http://www.ubuntuforums.org/showthread.php?t=172337](http://www.ubuntuforums.org/showthread.php?t=172337)

---

