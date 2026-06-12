---
title: "Black box in corner of screen"
date: 2008-07-19
forum: Apple Hardware Users
---

### Post by Crusty on 2008-07-19
I'm sure others have come across this, but I can't find a thread about it. I've got Hardy running on my ancient Pismo, and everything appears to be running correctly except there's a little black box in the upper left corner of the display that won't go away. It shows above any windows or panels. I think it has to do with X11, but I'm not sure how to deal with it.

Here's my xorg.conf file:

```
Section "Module"
	Load "GLcore"
	Load "bitmap"
	Load "dbe"
	Load "ddc"
	Load "dri"
	Load "extmod"
	Load "freetype"
	Load "glx"
	Load "int10"
	Load "record"
	Load "speedo"
	Load "type1"
	Load "v4l"
	Load "vbe"
	Load "xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:lwin_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"ati"
	BusID		"PCI:0:16:0"
	Option		"DynamicClocks"	"true"
	Option		"UseFBDev"	"true"
	Option 		"AGPMode" 	"2"
	Option 		"SWCursor"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 	16
	SubSection 	"Display"
		Depth 	1
		Modes 	"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection 	"Display"
		Depth 	4
		Modes 	"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection 	"Display"
		Depth 	8
		Modes 	"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection 	"Display"
		Depth 	15
		Modes 	"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection 	"Display"
		Depth 	16
		Modes 	"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection 	"Display"
		Depth 	24
		Modes 	"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode 0666
EndSection
```

---

### Post by Crusty on 2008-07-19
While I'm at it, I also don't see the splash screen when I first boot up the comp. Instead I see a psychedelic light show on the screen until the Ubuntu login screen appears. Not sure how to fix this either.

---

### Post by joninkrakow on 2008-07-19
Could you maybe post a screen shot with that black square? 

I suspect it has something to do with Gnustep, but without seeing it I wouldn't know. Have you installed Gnustep or GWorkspace, or something related?

-Jon

---

### Post by Crusty on 2008-07-19
I don't have Gnustep or Gworkspace installed.

I've attached a screenshot. The box is always in the upper left corner of the screen no matter what is there. I have a window there in the screenshot so it's easier to see.

---

### Post by stream303 on 2008-07-20
> **Crusty said:**
> While I'm at it, I also don't see the splash screen when I first boot up the comp. Instead I see a psychedelic light show on the screen until the Ubuntu login screen appears. Not sure how to fix this either.

The splash screen is more of a bother than a help on ppc's - I have never seen it operate properly without a lot of work.

At the second-stage yaboot boot: prompt, you could stop the countdown by hitting -tab-, and using

```
Linux nosplash
```

as your kernel boot parameter.  If this works ok, (you'll see the dmesg boot lines instead of the splash screen), you can add "nosplash" (without quotes) to your append= lines in  /etc/yaboot.conf file, and make it permanent with sudo ybin -v -C /etc/yaboot.conf

Alternatively, you could just add nosplash to the end of what is already there in the append= lines in yaboot.conf, ybin it, and take it from there.

---

### Post by Crusty on 2008-07-20
> **stream303 said:**
> If this works ok, (you'll see the dmesg boot lines instead of the splash screen), you can add "nosplash" (without quotes) to your append= lines in  /etc/yaboot.conf file, and make it permanent with sudo ybin -v -C /etc/yaboot.conf

Alternatively, you could just add nosplash to the end of what is already there in the append= lines in yaboot.conf, ybin it, and take it from there.

Thanks for the help. If I can't get it working, I'll end up doing this. Thing is, I had Feisty on here previously and it showed the splash screen just fine. I had to do some tweaking to yaboot.conf to get it working, but I can't remember what I did. It was a while back. It's not the same hard drive either, so I can't take a look at the old one. :(

---

