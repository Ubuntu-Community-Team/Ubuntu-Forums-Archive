---
title: "Problem with TV-out."
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by warpen on 2006-11-05
Hi.

I'm using Ubuntu 6.06 LTS and my TV-out has been working perfectly. But recently it hasn't and I suspect it started after an upgrade Ubuntu did. I don't know what kind of upgrade is was since it downloaded and installed a lot of packages...as you can see, I'm quite the newbie ;)

Anyway, it doesn't work now. My TV is just blank. I'm using an S-video cable. If anyone can help I will be most grateful :D 

Thanks.

---

### Post by warpen on 2006-11-05
Here is my xorg.conf...if you need it:

```

#Section "InputDevice"
#	Identifier  "Configured Mouse"
#	Driver      "mouse"
#	Option	    "CorePointer"
#	Option	    "Device" "/dev/input/mice"
#	Option	    "Protocol" "ExplorerPS/2"
#	Option	    "ZAxisMapping" "4 5"
#EndSection
#Section "InputDevice"
                                                      # /dev/input/event
                                                      # for USB
#	Identifier  "stylus"
#	Driver      "wacom"
#	Option	    "Device" "/dev/wacom"          # Change to 
#	Option	    "Type" "stylus"
#	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection
#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#	Identifier  "eraser"
#	Driver      "wacom"
#	Option	    "Device" "/dev/wacom"          # Change to 
#	Option	    "Type" "eraser"
#	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection
#Section "InputDevice"
                                                      # /dev/input/event
                                                      # for USB
#	Identifier  "cursor"
#	Driver      "wacom"
#	Option	    "Device" "/dev/wacom"          # Change to 
#	Option	    "Type" "cursor"
#	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

Section "ServerLayout"

#	InputDevice    "stylus" "SendCoreEvents"
#	InputDevice    "cursor" "SendCoreEvents"
#	InputDevice    "eraser" "SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
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
	Option	    "XkbLayout" "se"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "evdev"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/event9"
EndSection

Section "Monitor"
	Identifier   "SyncMaster"
	HorizSync    30.0 - 81.0
	VertRefresh  50.0 - 100.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "TVFormat" "PAL-B"
	Option	    "TVStandard" "VIDEO"
	Option	    "ForceMonitors" "tv"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480" "480x360" "400x300"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480" "480x360" "400x300"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480" "480x360" "400x300"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480" "480x360" "400x300"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480" "480x360" "400x300"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480" "480x360" "400x300"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

---

