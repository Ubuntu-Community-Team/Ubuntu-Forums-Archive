---
title: "ibook G3 dualUSB resolution problem"
date: 2006-08-07
forum: Apple PPC Users
---

### Post by miles128 on 2006-08-07
hi 

im a total newbie really but iv successfully switched to to Ubuntu and all  seems to be working fine in fact im using it now to type this post! However there is one really annoying problem and that is i cant change the resolution above 640x480. Iv tried following fixes in other threads regarding the  xorg.conf file but i haven't got any lines with "HorizSync" and "VertRefresh" in to change ?

Anyone got any ideas else im going to have to switch back to the old OS :(  

thanks

---

### Post by avtolle on 2006-08-07
OK, I'm not too sure what you have and haven't read and tried. The following is my suggestion:

At terminal, after backing up your /etc/X11/xorg.conf file, type in sudo gedit /etc/X11/xorg.conf scroll down to section "Monitor"; that is where the horizontal and vertical refresh sections are in mine; make any changes desired; then, scroll down to section "Screen", where you can add the additional resolutions. Once this is done, save your changes, exit gedit, then restart X, as I'm sure you have seen in other threads.
If you have done all this, and cannot find the lines in question, then I have no answer; perhaps those more knowledgeable than I can step in with further suggestions.  HTH.

---

### Post by x2l2 on 2006-08-07
i have one white ibook g3 too , i dont make anything special to change my screen resoloution but this is my /etc/X11/xorg.conf monitor and screen section:

```


Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Driver          "ati"
        BusID           "PCI:0:16:0"
        Option          "UseFBDev"              "true"
EndSection


Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection


```

---

### Post by avtolle on 2006-08-07
I have a G4 Cube with a 15" LCD. Here is the relevant part of my /etc/X11/xorg.conf file:
```

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Apple Studio"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
	Monitor		"Apple Studio"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

```

Hope this will help someone.

---

### Post by miles128 on 2006-08-07
Thanks for the replies and xorg.conf  copies, I'll have a go tomorrow at altering my xorg.conf file aswell as posting my broken file as my ibook isnt with me at the moment. Again thank you for your replies its nice to see a friendly and active communtiy :-D

---

### Post by avtolle on 2006-08-07
You are most welcome. Good luck!

---

### Post by miles128 on 2006-08-08
heres my version of things before iv tried changeing anything 


Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Color LCD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Monitor		"Color LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by miles128 on 2006-08-08
FIXED :D !

even though iv had this little problem its still been one of the smoothest instillations of an OS iv ever done and it all seems to be running fine now. Thanks to both the xorg.conf files above i altered my screen section to:

Section "Monitor"
	Identifier	"Color LCD"
	Option		"DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Monitor		"Color LCD"
	DefaultDepth	24
        SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubsection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection


Thanks to all :D

---

### Post by avtolle on 2006-08-08
Thanks for posting your fix. This will be helpful to others searching for resolution of similar problems.

---

### Post by archie_ on 2006-11-03
Many thanks for this posting! Strange that it doesn't pick up the  HorizSync and VertRefresh values when installing, but now it works great! 

Thanks again!

---

### Post by saracen on 2007-05-24
Yes!  This works!  I've been looking for a fix for a while now.  Thanks for posting the solution :)

---

