---
title: "Fullscreen not working in Hardy"
date: 2008-09-27
forum: Apple Hardware Users
---

### Post by Baaa on 2008-09-27
Hey everybody!
First of all, sorry for my english.

I'm using Ubuntu Hardy on a ppc mac mini, and if i try to view movies, or to play some games in full-screen mode, display is go away for a second, and then, the login screen come up.

Here is my Xorg.conf:

> 
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
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
	Load  "GLcore"
	Load  "dbe"
	Load  "dri"
	Load  "extmod"
	Load  "glx"
	Load  "record"
	Load  "xtrap"
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
	HorizSync     31-110
	VertRefresh    85

EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "KGAUniversal"       	# [<bool>]
	Identifier  "Card0"
	Driver      "ati"
	VendorName  "ATI Technologies Inc"
	BoardName   "RV280 [Radeon 9200]"
	BusID       "PCI:0:16:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth    24	
	SubSection "Display"
		Viewport   0 0
		Depth     1
		Modes "1280x1024" "1024x768" "800x600" "640x480"	
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
		Modes "1280x1024" "1024x768" "800x600" "640x480"	
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
		Modes "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
		Modes "1280x1024" "1024x768" "800x600" "640x480"	
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes "1280x1024" "1024x768" "800x600" "640x480"	
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


---

### Post by BryannPaulaMelvin on 2008-09-28
I am not sure if this is an X problem:

If the movies and games you are talking about are on the internet: and you have an opensource flash substitute installed, it may be the problem:

I have noticed gnash crash gnome before on Feisty...I haven't seen it in Hardy yet.

---

### Post by mfox on 2008-09-28
What size is your monitor?  The maximum size noted in your xorg.conf file is 1280x1024.  Does your regular Ubuntu desktop take up the full monitor space?  If so, I don't think the issue is Hardy in general or xorg.conf in particular.  It may be the program you are using to run the movies or games, or as BryannPaulaMelvin suggested, it may be a plug-in.

---

