---
title: "how to hook a laptop up to the tv using a s video cable"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by jwalkeraz84 on 2007-01-23
i have a dell inspiron 630m, it has a s-video hookup on the left handside, so i ran it from the laptop to the tv, when the turn the tv to the correct video setting i get a black screen, i was wondering what i need to do to make this work?

i am new to ubuntu and i really need some help

---

### Post by Jamesbowden on 2007-01-23
I asked this exact same question about a week ago, unfortunatly the anser seemed to be, you cant, or its very hard. one guy told be just reboot you computer with the cable plugged in, you can give it a try, but it didnt work for me. hopefully your post will get some better answers.

---

### Post by Jamesbowden on 2007-01-23
Sorry to post again:

[http://ubuntuforums.org/showthread.php?t=331473](http://ubuntuforums.org/showthread.php?t=331473)

heres my post if it helps.

---

### Post by punx45 on 2007-01-23
you need to do a little tweaking before you can do this:

most likely you will need to install a new driver and then edit your xorg.conf file to add the second screen (tv).   

it will all depend on your hardware.

in a terminal:
```
lspci | grep -i vga
```

if that returns nothing, do just 'lspci' and then read the output carefully for a line that indicates a video card.  it should tell you the make/model or chipset of the video card.

then you can search the forum specifically for that hardware.

---

### Post by mexlinux on 2007-01-23
I have the same laptop.
Whithout installing any new driver, in edgy, I got it working with the following xorg.conf
(back up yours first!).
I found that xorg.conf somewhere in this forum....
Just disable one of the server layouts in order to use the other:
> 
	Option "DefaultServerLayout" "LCDandTV"
 	#Option "DefaultServerLayout" "LCD"


Notes: 
-Beryl does not work when I enable the LCDandTV layout.
-The TV is below the LCD

The Original file used SVIDEO instead of Composite in 
 	Option "TVOutFormat" "
Nevertheless for me that gave me just black and white, thats why I use composite.
Here it is:

> 
Section "Files"
	 FontPath "/usr/share/X11/fonts/misc"
 	FontPath "/usr/share/X11/fonts/cyrillic"
 	FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
 	FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
 	FontPath "/usr/share/X11/fonts/Type1"
 	FontPath "/usr/share/X11/fonts/100dpi"
 	FontPath "/usr/share/X11/fonts/75dpi"
 	# path to defoma fonts
 	FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
 EndSection
 
 
Section "Module"
	 Load "bitmap"
 	Load "ddc"
 	Load "dri"
 	Load "extmod"
 	Load "freetype"
 	Load "glx"
 	Load "int10"
 	Load "type1"
 	Load "v4l"
 	Load "vbe"
 	Load "synaptics"
 	Load "dbe"
EndSection
 
Section "InputDevice"
	 Identifier "Generic Keyboard"
 	Driver "kbd"
 	Option "CoreKeyboard"
 	Option "XkbRules" "xorg"
 	Option "XkbModel" "pc104"
 	Option "XkbLayout" "latam"
EndSection
 
Section "InputDevice"
	 Identifier "Configured Mouse"
 	Driver "mouse"
 	Option "CorePointer"
 	Option "Device" "/dev/input/mice"
 	Option "Protocol" "ExplorerPS/2"
 	Option "ZAxisMapping" "4 5"
 	Option "Emulate3Buttons" "true"
EndSection
 
Section "InputDevice"
	 Identifier "Synaptics Touchpad"
 	Driver "synaptics"
 	Option "SendCoreEvents" "true" 
 	Option "Device" "/dev/psaux"
 	Option "Protocol" "auto-dev"
 	#Option "LeftEdge" "1700"
 	#Option "RightEdge" "4900"
 	#Option "TopEdge" "1700"
 	#Option "BottomEdge" "4200"
 	#Option "FingerLow" "25"
 	#Option "FingerHigh" "30"
 	Option "MaxTapTime" "10"
 	Option "MaxTapMove" "20"
 	#Option "VertScrollDelta" "100"
 	Option "HorizScrollDelta" "0"
 	#Option "MinSpeed" "0.30"
 	#Option "MaxSpeed" "0.45"
 	#Option "AccelFactor" "0.0030"
	 Option "SHMConfig" "on"
 	Option "Repeater" "/dev/ps2mouse"
EndSection
 
Section "Device"
	 Identifier "Intel Corporation Intel Default Card"
 	Driver "i810"
 	BusID "PCI:0:2:0"
	Option  	"XAANoOffscreenPixmaps"	#Añadido paraa Beryl
EndSection
 
Section "Device"
	 Identifier "LCD"
 	Driver "i810"
 	Option "MonitorLayout" "TV,LFP"
 	Screen 0
 	BusID "PCI:0:2:0"
EndSection
 
Section "Device"
	 Identifier "TV"
	 Driver "i810"
 	Option "MonitorLayout" "TV,LFP"
 	Option "TVStandard" "NTSC"
 	Option "TVOutFormat" "Composite" #"SVIDEO"
 	Option "ConnectedMonitor" "TV"
 	Screen 1
 	BusID "PCI:0:2:0"
EndSection
 
Section "Monitor"
	 Identifier "LCD"
 	Option "DPMS"
 	Modeline "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection
 
Section "Monitor"
	 Identifier "TV"
 	HorizSync 30-50
 	VertRefresh 60
EndSection
 
Section "Screen"
	 Identifier "LCD"
 	Device "LCD"
 	Monitor "LCD"
 	DefaultDepth 24
 	SubSection "Display"
	 	Depth 1
 		Modes "1280x800"
 	EndSubSection
 	SubSection "Display"
 		Depth 24
 		Modes "1280x800"
 	EndSubSection
EndSection
 
 
Section "Screen"
	 Identifier "TV"
 	Device "TV"
 	Monitor "TV"
 	DefaultDepth 24
 	Subsection "Display"
	 	Depth 24
 		Modes "1024x768"
 	EndSubsection
EndSection
 
Section "ServerLayout"
	 Identifier "LCDandTV"
 	Screen 0 "LCD"
 	Screen 1 "TV" Below "LCD"
 	InputDevice "Generic Keyboard"
 	InputDevice "Configured Mouse"
 	InputDevice "Synaptics Touchpad"
 	#Option "Clone" "On"
 	Option "Xinerama" "True"
EndSection
 
Section "ServerLayout"
	 Identifier "LCD"
 	Screen "LCD"
 	InputDevice "Generic Keyboard"
 	InputDevice "Configured Mouse"
 	InputDevice "Synaptics Touchpad"
EndSection
 
Section "ServerFlags"
	#Option "DefaultServerLayout" "LCDandTV"
 	Option "DefaultServerLayout" "LCD"
EndSection
 
Section "DRI"
	 Mode 0666
EndSection 

#Esta desabilitado, yo lo habilite 
Section "Extensions"
	 Option "Composite" "enable"
EndSection



---

### Post by featherking on 2007-02-20
I wrote up an actual 'How To' for this and it is posted [[COLOR="Red"]here[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=361124"). It helps to switch between a few different xorg files so you can have one to use svideo, one for dual monitors, one for using a projector, etc.. I use it all the time on my i945 chipset but it should work with any intel board using the i810

---

