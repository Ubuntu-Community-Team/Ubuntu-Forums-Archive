---
title: "Can't get iMac G5 to boot from Unbuntu burned cd"
date: 2007-08-25
forum: Apple PPC Users
---

### Post by Jordgurney on 2007-08-25
Hi, I downloaded the latest Unbuntu for power pc mac's, burned it onto a dvd-r, and tried booting from it. If I hit enter it boots to a black screen  with nothing. Theres also a live boot=ofonly or something like that. When  I try that it boots, I get a off centered, Unbuntu logo and name in negative colors. its loads full and then boots to a pitch black screen and my fans whirl up. I have no clue what to do and I am really excited about trying out Unbuntu and possible Unbuntu Ultimate, Linux MCE and others. 
Btw its in the title but...Its a iMac G5. :confused:

---

### Post by Auria on 2007-08-25
Did you burn the CD very slowly? when it's a system the smallest error during burn can cause it to stop working...

if no one else has better solutions to try first, you might want to try the alternate CD. It's not as shiny (it's text-based) but it's more reliable and also makes trouble-shooting easier.

---

### Post by Jordgurney on 2007-08-25
I beleive i burned it at 2x.  Do you mean by CD as in another distribution?

---

### Post by Auria on 2007-08-25
> **Jordgurney said:**
> Do you mean by CD as in another distribution?

ubuntu has 2 different kinds of installers available. There is the LiveCD that allows you to boot it and try it before you install. There is also the alternate CD that goes straight ahead into a text-based installer. These 2 CDs should be available for download AFAIK. Problem is with LiveCD, since it's graphical, if your grpahical configuration doesn't work out-of-the-box, it crashes and is unusable. The alternate CD being text-based, it will allow you to configure the graphics instead of crashing (unfortunately i myself cannot help you with that, but i'm sure someone else will, there are very knowledgeable people here)

---

### Post by Jordgurney on 2007-08-25
Ahh Thanks I am downloading the alternate installer now :) Maybe someone else has some answers?

---

### Post by Jordgurney on 2007-08-26
I tried the alternate installer. I found that both cd's work. But when the livecd gots to unbuntu it shows "Unbuntu" In negatives and in the upper left corner. Then the screen goes black but i get the log in sounds. Same with alternate install just the unbuntu is centered and its bigger. I hope this can help out and that it should be able to fix.

---

### Post by ndunn on 2007-08-27
Do you have a built-in iSight?

This sounds exactly like the problem I had installing on my iMac G5 with the built-in iSight. It's an issue with the drivers for the graphics card. I had to install the server install, manually edit xorg.conf, and then aptitude emerge ubuntu-desktop. This is the xorg.conf that got it working.

```

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:lwin_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Driver		"ati"
	BusID		"PCI:4:0:0"
	Option	"ReverseDDC"	"On"
	Option	"DDCMode"	"On"
	Option	"PanelSize"	"1440x900"
	#Option	"AccelMethod"	"EXA"
	Option "UseFBDev" "On"	
	Option	"MonitorLayout"	"TMDS,NONE"
EndSection

#Section "Monitor"
#	Identifier	"Color LCD"
#	VendorName	"APP"
#	ModelName	"Color LCD"
#	Option		"DPMS"
#	HorizSync	28-72
#	VertRefresh	43-60
#EndSection

# EDID version 1 revision 3
Section "Monitor"
         # Block type: 2:0 3:1
         # Block type: 2:0 3:fe
         # Block type: 2:0 3:fc
         Identifier "Color LCD"
         VendorName "APP"
         ModelName "Color LCD"
         # Block type: 2:0 3:1
         # Block type: 2:0 3:fe
         # Block type: 2:0 3:fc
         # DPMS capabilities: Active off:yes  Suspend:no  Standby:no
         Mode    "1440x900"      # vfreq 59.983Hz, hfreq 54.525kHz
                 DotClock        109.050000
                 HTimings        1440 1488 1520 2000
                 VTimings        900 903 906 909
                 Flags   "-HSync" "-VSync"
         EndMode
         # Block type: 2:0 3:1
         # Block type: 2:0 3:fe
         # Block type: 2:0 3:fc
EndSection
                                                                     
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Monitor		"Color LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Jordgurney on 2007-08-28
Yea it is a iSight iMac. So I install the server edition and edit that and it should work?

---

### Post by ndunn on 2007-08-29
Yeah, that worked for me, but I couldn't find much about it using Google, so I'm not sure how universal it is. You've got to install ubuntu-desktop before you edit though, otherwise xorg.conf won't exist. I had the directions reversed before.

---

