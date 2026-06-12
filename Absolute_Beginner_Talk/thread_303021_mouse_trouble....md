---
title: "mouse trouble..."
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by serosis on 2006-11-19
well i have an interesting problem...

whenever Ubuntu is loading up, be it from the HD or the Live CD my mouse gets disabled or something and doesn't work.

I know the mouse works cause obviously I got Ubuntu installed with no problem, and it works in WinXP. I wanna know why it's doing this and how to fix it.

Any help is greatly appreciated

---

### Post by serosis on 2006-11-19
nobody?

then i guess i'll have to buy a PS/2 mouse to test it

---

### Post by ReaderRat on 2006-11-19
I gather that you are using a desktop machine. I use a USB mouse with both laptop & desktop - okay.Try posting a copy of your xorg.config file in your next post:
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by serosis on 2006-11-20
good thing is that i don't need to boot into ubuntu to get this file

> 
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
	Load	"i2c"
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
	Identifier	"ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"e15t4"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"e15t4"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


there ya go

---

### Post by serosis on 2006-11-20
anybody?

---

### Post by al_sharpe on 2006-11-21
Hello serosis:

The simple answer is unplug the wacom tablet.
It seems to conflict with mice
Then if you want to use tablet, plug it in and live without mouse.
The mouse and tablet fight for mouse0 on boot up and either could
win, it seems
run this in terminal mode 
sudo xxd /dev/input/mouse0
move mouse around in terminal window, if you see lines appear
that is mouse0, you could then try tablet mouse in same window
changing to mouse1 in above line.

If I find a way for both to play well together, will post
to date no luck

Yes I have found the ploblem with the wacom anyway
is should read /dev/input/wacom not /dev/wacom 

What mouse are you using, out of curiosity. 

Al Sharpe

---

### Post by serosis on 2006-11-21
I don't have a wacom tablet...

all i have trouble with is when Ubuntu loads up (Ubuntu logo with status bar) the mouse just shuts off

and thats all i need fixed, other than that Ubuntu runs flawlessly

---

### Post by serosis on 2006-11-22
nobody with similar problem or a solution? :-(

---

### Post by mgmiller on 2006-11-22
Have you tried plugging the USB mouse into a different port?  If you have them try ports not on your motherboard, but on a PCI expansion card.  Try looking in your BIOS and find a section that says enable legacy USB and disable it.  (This last tip has fixed USB mouse issues for me in the past).

Good luck.

---

### Post by serosis on 2006-11-22
Cool thanks for the advice, i actually never thought of doing that (switching ports), nor did i even consider disabling the legacy support.


Another thing, my mouse works under the Dapper desktop cd (or live cd, or if the are in fact the same) if that counts for anything.

---

### Post by serosis on 2006-11-23
i think i found the problem, my Ubuntu doesn't have a "/dev/input/" folder which i noticed that the xorg.conf was pointed to "/dev/input/mice".

and the thing that sucks is that i can't copy over the input folder from the live cd because i am not the "owner".

this blows tremendously.

---

