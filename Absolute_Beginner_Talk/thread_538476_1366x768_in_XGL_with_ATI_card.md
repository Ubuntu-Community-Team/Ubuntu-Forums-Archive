---
title: "1366x768 in XGL with ATI card"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by verticalgain1 on 2007-08-30
Hello

I have a Radeon X800 graphics card.  I've reinstalled Feisty and Beryl according to the guide for my machine.

Up until a few days ago when I had to wipe and reinstall I had Beryl running on XGL with my ATI card in 1366x768.  Since the reinstallation I cannot get it to perform in this resolution.

I've tried editing my xorg.conf file, here is a copy:

> 

Section "ServerLayout"

	Identifier     "Default Layout"

	Screen         "Default Screen" 0 0

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



Section "ServerFlags"

	Option	    "AIGLX" "off"

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

	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY

EndSection



Section "InputDevice"

	Identifier  "eraser"

	Driver      "wacom"

	Option	    "Device" "/dev/input/wacom"

	Option	    "Type" "eraser"

	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY

EndSection



Section "InputDevice"

	Identifier  "cursor"

	Driver      "wacom"

	Option	    "Device" "/dev/input/wacom"

	Option	    "Type" "cursor"

	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY

EndSection



Section "Monitor"

	Identifier   "Generic Monitor"

	HorizSync    30.0-61.0

	VertRefresh  60.0-75.0

	Option	    "DPMS"

EndSection



Section "Device"

	Identifier  "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"

	Driver      "fglrx"

	Option	    "VideoOverlay" "on"

	Option	    "OpenGLOverlay" "off"

	BusID       "PCI:1:0:0"

EndSection



Section "Screen"

	Identifier "Default Screen"

	Device     "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"

	Monitor    "Generic Monitor"

	DefaultDepth     24

	SubSection "Display"

		Depth     1

		Modes    "1366x768" "1024x768" "800x600" "640x480"

	EndSubSection

	SubSection "Display"

		Depth     4

		Modes    "1366x768" "1024x768" "800x600" "640x480"

	EndSubSection

	SubSection "Display"

		Depth     8

		Modes    "1366x768" "1024x768" "800x600" "640x480"

	EndSubSection

	SubSection "Display"

		Depth     15

		Modes    "1366x768" "1024x768" "800x600" "640x480"

	EndSubSection

	SubSection "Display"

		Depth     16

		Modes    "1366x768" "1024x768" "800x600" "640x480"

	EndSubSection

	SubSection "Display"

		Depth     24

		Modes    "1366x768" "1024x768" "800x600" "640x480"

	EndSubSection

EndSection



Section "DRI"

	Mode         0666

EndSection



Section "Extensions"

	Option	    "Composite" "Disable"

EndSection




I went in and manually changed the xorg to have the 1360x768 line, as seen above.  The horizontal and vertical syncs are also custom to my monitor as per it's manual.

I've been over every FAQ and howto I can find and nothing seems to be fixing this.  Does anyone have any other suggestions?  Let me know and I can post more info if necessary.

---

### Post by verticalgain1 on 2007-08-30
Anyone?  It worked for me before, and I know other people are doing this exact thing.   Please let me know what I should do.

---

