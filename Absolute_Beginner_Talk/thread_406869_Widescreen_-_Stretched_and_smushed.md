---
title: "Widescreen - Stretched and smushed"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by awiggin on 2007-04-11
Hey all,

I am close to getting everything working in Ubuntu so I wouldn't hardly ever have to go back to my other OS.

But the widescreen thing is really bothering me.  I have a 19" widescreen monitor from Envision.  The desktop is stretched and everything is smushed.  I have tried several things, including editing xorg.conf, but nothing has happened.

Actually, that isn't totally true.  The desktop is the same, but the login window is super-inflated and looks weird so I guess that is a step backward.

I have also tried to add my widescreen resolution (1440X900) to 915resolution but that didn't work.

Is it a driver issue?  If so, how do I find that out and how would I fix it?

Thanks and peace,
Lance

---

### Post by awiggin on 2007-04-11
bump

---

### Post by Bachstelze on 2007-04-11
You used 915resolution but are you sure you have an Intel graphics adapter ?

---

### Post by awiggin on 2007-04-11
I think I have an Intel Graphics adapter.  How would I find out for sure?

---

### Post by Bachstelze on 2007-04-11
```
lspci | grep VGA
```

for example. If you do have an Intel adapter, 915resolution is indeed the way to go but I'm afraid I cannot help yo about usin it...

---

### Post by ahaslam on 2007-04-11
Please post your xorg.conf, I had similar issues & may be able to help.

---

### Post by awiggin on 2007-04-11
I will check when I get home to my ubuntu machine.

I thought, when looking at that before that it said I had a Intel 945G/GZ - Does that sound possible.  (Total noob here, so I am not sure if I am sharing the right information.)

Thanks,
L

---

### Post by ahaslam on 2007-04-11
Don't know, Nvidia user :p 

What you'll want to look for is: 
> 
Option         "metamodes" "1440x900 +0+0

Under Section "Screen"

---

### Post by awiggin on 2007-04-11
Here is my xorg.conf as it currently is:

Sorry for including everything, but I am not exactly sure what you are looking for, so I didn't want to leave anything out.

THanks for helping with this.

```

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
	Identifier	"Intel Corporation 945G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"G19LWk"
	Option		"DPMS"
	HorizSync	30-60
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 945G Integrated Graphics Controller"
	Monitor		"G19LWk"
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
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by awiggin on 2007-04-11
bump

---

### Post by awiggin on 2007-04-12
I got it!  WOOHOO!

My printer works, my widescreen works.  Only one more issue -

The dreaded usb wifi adapter.

I am determined to get this one to work as well.

Peace!  And thanks for all the help.

-Lance

---

### Post by disandov on 2007-04-12
So how could you fix it?
I have a similar issue and tried almost everything :(

---

### Post by awiggin on 2007-04-12
Believe me, I tried everything I found on almost every thread. I found this solution and it was entitled something like "Easy Widescreen fix".  And it was - I was amazed.

FIrst of all, I have an intel chipset in my monitor and I'm not sure what kind of video card - it's probably pretty generic.

FIrst, I opened 915resolution.  I think the command was

915resolution -l

I changed one of the modes (I picked mode 30, which was listed as 800X640 or something I knew I would never use).  I was told not to change one of the higher ones as it could be disastrous.  Anyhow - while in 915resolution, I typed:

915resolutino 30 1440 900

just like that (You type in different resolutions of course if your screen is a different size).

Then I edited xorg.conf (I am pretty sure this was the next step).

Where it said

Mode=auto , I changed it to Mode=30 (the number of the mode I altered).

Then I changed XRESO and YRESO to

XRESO=1440
YRESO=900

Then I restarted my computer and it was fixed (well, almost).

My screen was off-center so I had to adjust the buttons on the computer screen manually a little bit.

But it worked - and it was way easier than what I had tried before.

Let me know if it works.

-Lance

---

### Post by Ctrl-Z on 2007-08-25
**awiggin**, I also have Envision G19LWk monitor and am fighting for a best picture in Ubuntu right now. Can you post you current monitor mode here for me to compare, please? You can reach it by entering monitor menu (pressing button "1" near monitor power button) and selecting "Information" (fourth from top).

Here is what I currently have and how I get there will follow:
HFreq: 56.47 kHz
VFreq: 59.69 Hz
Pixel Clock: 85.45 MHz
Resolution: **1152x900**

What bothers me is the resolution (and some blurness), because under Windows, where everything looks ok) what I get looks like here:
HFreq: 55.68 kHz
VFreq: 59.61 Hz
Pixel Clock: 106.62 MHz
Resolution: **1440x900**

I have relatively old  videocard (nVidia RIVA TNT2 NV5M64) and I hope this is not the source of problem. Here is what I did (since regular dpkg reconfig got me in even worse settings): I went to [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) and using Pixel Clock from Windows compiled several Modelines. One of them gave me more or less tolerable result with posted above results. Using specs from Envision web site [http://www.envisiondisplay.com/products/specsheets/g19lwk-specs.pdf](http://www.envisiondisplay.com/products/specsheets/g19lwk-specs.pdf) did not help much either.

I hope it won't be too much trouble for you to post your monitor mode info here! :)
Thanks.

---

