---
title: "xinerama problems"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by oostatoo on 2006-11-07
I am having trouble getting my second monitor to work. I am running a Dell Latititude D620 Laptop. The external monitor is a Dell E773s. My OS is Edgy. The Problem is that I have messed with my xorg.conf quite a bit and for some reason it wont even recognize my external monitor. It is "on" but it wont display a thing. The video card is an intel 950 I believe.

Here is my xorg.conf minus all the comments on the top:

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"Intel"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Laptop LCD"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Monitor"
	Identifier	"Dell E773s"
	Option		"DPMS"
	Option 		"NoDDC"
	HorizSync 	30-75
	VertRefresh 	50-160
EndSection

Section "Screen"
	Identifier	"Laptop Screen"
	Device		"Intel"
	Monitor		"Laptop LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x800" "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Dell E773s Screen"
	Device		"Intel"
	Monitor		"Dell E773s"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x800" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Laptop Screen"
	Screen		"Dell E773s Screen" RIGHTOF "Laptop Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerFlags"
	    Option "Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection


Please let me know what im doing wrong.](*,) 

Thanks in advance,
Eddie

---

### Post by TheMono on 2006-11-07
Try changing 

Section "Device"
Identifier "Intel"
Driver "i810"
BusID "PCI:0:2:0"
Screen 0
EndSection

to 

Section "Device"
Identifier "Intel"
Driver "i810"
BusID "PCI:0:2:0"
Screen 0
Option "MonitorLayout" "CRT,LFP"
EndSection



That's the only thing I can see from a brief skim.

---

### Post by TheMono on 2006-11-07
I tell a lie - another change. Both your devices are named Intel - not good. Change the second one to Intel2 (or anything really, but Intel2 is easy lol)

You'll need to change it in the device section, and the screen section, so that 

Section "Device"
Identifier "Intel"
Driver "i810"
BusID "PCI:0:2:0"
Screen 1
EndSection

Becomes 


Section "Device"
Identifier "Intel2"
Driver "i810"
BusID "PCI:0:2:0"
Screen 1
EndSection



And, 


Section "Screen"
Identifier "Dell E773s Screen"
Device "Intel"
Monitor "Dell E773s"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1440x900" "1280x800" "1024x768" "800x600"
EndSubSection
EndSection


Becomes,


Section "Screen"
Identifier "Dell E773s Screen"
Device "Intel2"
Monitor "Dell E773s"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1440x900" "1280x800" "1024x768" "800x600"
EndSubSection
EndSection

---

### Post by CatKiller on 2006-11-07
Having meaningful Identifiers might help: ```
Section "Device"
Identifier "**0**Intel"
Driver "i810"
BusID "PCI:0:2:0"
Screen 0
EndSection

Section "Device"
Identifier "**1**Intel"
Driver "i810"
BusID "PCI:0:2:0"
Screen 1
EndSection
```
```
Section "Screen"
Identifier "Laptop Screen"
Device "**0**Intel"
Monitor "Laptop LCD"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1440x900" "1280x800" "1024x768"
EndSubSection
EndSection

Section "Screen"
Identifier "Dell E773s Screen"
Device "**1**Intel"
Monitor "Dell E773s"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1440x900" "1280x800" "1024x768" "800x600"
EndSubSection
EndSection
```

EDIT: Beaten to it because the kettle boiled. **sigh**

---

### Post by oostatoo on 2006-11-07
Success. Well partly. The second screen is on! But, I can only drag windows about halfway into the screen on the right. So I have a firefox windows half and half on both screens. However I can have the firefox window fully maximized on the laptop screen if I want. If this makes any difference my background image isn't centered on the external screen.

Thanks much for the help!

Edit: Just so you guys know my laptop screen is wide screen. The model again is Dell Latitude D620. I can stretch a window to full screen but when i shrink it the right side moves in with the left.

---

### Post by oostatoo on 2006-11-07
Here is my "NEW" xorg.conf:

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier 	"Intel"
	Driver 		"i810"
	BusID 		"PCI:0:2:0"
	Screen 		0
	Option 		"MonitorLayout" "CRT,LFP"
EndSection

Section "Device"
	Identifier	"Intel2"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Laptop LCD"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Monitor"
	Identifier	"Dell E773s"
	Option		"DPMS"
	#Option 		"NoDDC"
	HorizSync 	30-70
	VertRefresh 	50-160
EndSection

Section "Screen"
	Identifier	"Laptop Screen"
	Device		"Intel"
	Monitor		"Laptop LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Dell E773s Screen"
	Device		"Intel2"
	Monitor		"Dell E773s"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Laptop Screen"
	Screen		"Dell E773s Screen" RIGHTOF "Laptop Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "ServerFlags"
	    Option "Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

BTW, Dell says I can get 1440x900 res on this laptop screen but it only lets me use 1280x800. I have installed 915resolution through synaptic but do I need to do anything special?

Thanks again PeePs!

---

### Post by mbeierl on 2006-11-07
I too had a working xinerama config in dapper.  I did a fresh install of edgy and am working on moving my preferences from dapper to edgy.

So, I brought my xorg.conf forward - restart X and great! the second monitor shows up perfectly!  Except! same problem: the windows seem to be bound to the confines of the first monitor.  The mouse can move onto the second, but windows stop part-way.

Anyone have any ideas what's causing this?  I think it might have something to do with the randr because now I can use the screen resolution applet to rotate the primary display, leaving the secondary at its original orientation.

Secondly, oostatoo, I am sorry to tell you, but if you've got the Intel chipset, your maximum laptop resolution is 1280x800.  You'd need the nvidia chipset to get the higher resolution.

---

### Post by oostatoo on 2006-11-07
I figured out it has something to do with the size of the window. If i manually maximize the window on my laptop screen i can drag it over all the way to the end of the external screen. But the left edge of the screen still hangs over to the laptop screen.

---

### Post by CatKiller on 2006-11-07
> **oostatoo said:**
> Success. Well partly. The second screen is on! But, I can only drag windows about halfway into the screen on the right. So I have a firefox windows half and half on both screens. However I can have the firefox window fully maximized on the laptop screen if I want. If this makes any difference my background image isn't centered on the external screen.

It was that kind of thing that made me not use Xinerama - with two different resolutions it gets quite ugly quite quickly.

---

### Post by mbeierl on 2006-11-07
Xinerama worked excellently for me on my D620 with Dapper.  I had no problems with the two different resolutions - the windows would resize well, maximize appropriately, etc.  This seems to be an X 7.1 thing - or driver thing? I'm not sure.  The window hanging over on the laptop monitor - look at your mouse carefully when dragging - you'll actually see that the window "stops" at the edge of the primary display so as not to go "off" the screen.

It's as if the window manager believes the screen size to be 1280x800 instead of the xinerama merged size.  My workspace switcher applet shows the same thing.  It used to be twice as wide, showing the second display; now it only shows the windows in the primary display, constrained by the same aspect ratio as the primary display.

I'm sure there is a latent bug in here somewhere.  But it wouldn't be edgy if it all worked first try!  It would be an LTS release :)

Here's to getting to the root cause of this and making things better!

---

### Post by oostatoo on 2006-11-08
Is there a way to install the older version of X and give that a try?

---

### Post by oostatoo on 2006-11-08
Nevermind everyone I did lots of digging and found the solution right here on the forums. I deleted ~/.gconf/desktop/gnome/screen folder and poof it worked.

---

### Post by wammin on 2006-11-27
> **oostatoo said:**
> Nevermind everyone I did lots of digging and found the solution right here on the forums. I deleted ~/.gconf/desktop/gnome/screen folder and poof it worked.

I ran into this exact problem today, too and then I found this thread. Oostatoo's trick of deleting the screen folder worked for me!

Make sure to restart Ubuntu after deleting the folder. Just restarting X didn't work for me.

---

### Post by miseryshining on 2006-12-07
Ive been searching hours for this solution and it solved it for me as well! Thank you so much, i was at the point of giving up.

---

