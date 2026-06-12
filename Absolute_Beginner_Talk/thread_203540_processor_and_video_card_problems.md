---
title: "processor and video card problems"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by KudouUsagi on 2006-06-25
Alright I'm having 2 problems. 
The first one is that when I go into the device manager and look at procesor it says unknown next to everything. How do I get it to recognise my processor?
The second problem is that when I try to install the ATI drivers  when I check to see if it worked it says 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
I checked the xorg.conf and it does have Load  "dri" there so why isnt it working?

---

### Post by theduke11 on 2006-06-25
Im not sure about your first question but ive always used this guide to installing an ati driver and its always worked

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by johnc4510 on 2006-06-25
This info for the processor has never shown anything but unknown on my machines. To make sure your processor has been recognized correctly, type this into the terminal:
cat /proc/cpuinfo
The terminal is located here in gnome:
System>Accessories>Terminal

---

### Post by KudouUsagi on 2006-06-25
I have followed the guide for the ati drivers exactly and there is no change.

---

### Post by theduke11 on 2006-06-25
Kudo, im new and when i first tried to install the ati drivers i didnt use the guide i linked you too. I then used the guide i linked you to and yes it didnt work. I reinstalled linux and tried the guide that i linked you to first and it worked.

Im sure thats not what you want to hear and im sure there is a way to avoid reinstalling ubuntu to get the ati drivers to work but thats just what i did is all.

---

### Post by raptros-v76 on 2006-06-25
ok. first do sudo dpkg-reconfigure -phig xserver-xorg. then follow the installation guide

---

### Post by joshuapurcell on 2006-06-25
Posting the contents of this file may help:

**/etc/X11/xorg.conf**

---

### Post by KudouUsagi on 2006-06-25
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
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
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
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
	Identifier   "NEC LCD1565"
	HorizSync    31.0 - 60.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NI [Radeon 9800]"
	Driver      "vesa"
	VideoRam    131072
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "ATI Technologies, Inc. Radeon R350 NI [Radeon 9800]"
	Monitor    "NEC LCD1565"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

---

### Post by joshuapurcell on 2006-06-25
You have two Screen sections with the same name (I'm surprised the xserver doesn't fail with some error). Change this portion:```
Section "Screen"
Identifier "aticonfig-Screen[0]"
Device "ATI Technologies, Inc. Radeon R350 NI [Radeon 9800]"
Monitor "NEC LCD1565"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection
```To this:```
Section "Screen"
Identifier "aticonfig-Screen[0]"
Device "aticonfig-Device[0]"
Monitor "NEC LCD1565"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection
```
Since you are changing the first screen listed (and it is using that screen currently anyway) this should do it. You could also change the name of the second screen so that they have different names and don't rely on the order in which they are found in this file.

---

### Post by KudouUsagi on 2006-06-26
well I've tried intalling it about 5 times and I changed the /etc/X11/xorg.conf file.. but there is still no change.

---

