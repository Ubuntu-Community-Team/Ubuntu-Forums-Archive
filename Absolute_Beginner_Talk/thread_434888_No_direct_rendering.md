---
title: "No direct rendering"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by Cientista on 2007-05-06
I have updated from Ubuntu 6.10 to 7.04 and since them I lost my 3D hardware acceleration.
I search on internet about direct rendering, ATI drivers and so on, and its seems that nothing  works. I have edit my xorg.conf so many time that I don't have the original file anymore.
I have a laptop Toshiba A70 with a ATI Radeon Mobility 9000 (and I am sure that this card has 3D acceleration).
I tried to use the automatic xorg.cong selecting the ATI from the menu but still no Direct rendering.

Does anyone here could help me to get my 3D hardware acceleration back?

Thanks

---

### Post by overdrank on 2007-05-06
> **Cientista said:**
> I have updated from Ubuntu 6.10 to 7.04 and since them I lost my 3D hardware acceleration.
I search on internet about direct rendering, ATI drivers and so on, and its seems that nothing  works. I have edit my xorg.conf so many time that I don't have the original file anymore.
I have a laptop Toshiba A70 with a ATI Radeon Mobility 9000 (and I am sure that this card has 3D acceleration).
I tried to use the automatic xorg.cong selecting the ATI from the menu but still no Direct rendering.

Does anyone here could help me to get my 3D hardware acceleration back?

Thanks

Hi there is a sticky in the forum that address this issue
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)
Good luck!

---

### Post by Cientista on 2007-05-06
I tried also that!
When I use the command :

sudo aticonfig --initial

It returns me 

Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

As I said before, I tried so many things that I am not sure what is installed or not on my computer.

Any other things that I can try?

Thanks

---

### Post by overdrank on 2007-05-06
> **Cientista said:**
> I tried also that!
When I use the command :

sudo aticonfig --initial

It returns me 

Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

As I said before, I tried so many things that I am not sure what is installed or not on my computer.

Any other things that I can try?

Thanks

I am sorry I am not using feisty, the only thing I can recommend is return to edgy. That may not be a option for you but that is all I know.:(

---

### Post by FishRCynic on 2007-05-13
i have an A70 - 3d enabled
these are all bits and pieces collected from various postings 
in the Ubuntu forums.
below the bolded items are what i have added 

this is my device section in /etc/X11/xorg.conf


Section "Device"
	Identifier	"ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]"
#	Driver		"fglrx"
	[B]Driver		"radeon"
        Option 		"DRI" "true"[/B]
#	Option		"ColorTiling" "On"
	**Option          "EnablePageFlip" "true"**
#	Option		"AccelMethhod" "EXA"
	[B]Option		"XAANoOffscreenPixmaps"
	Option		"RenderAccel" "true"
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "true"
	Option		"DisableGLXRootClipping" "true"
	Option		"AddARGBGLXVisuals" "true"
	Option		"AllowGLXWithComposite" "true"[/B]
	BusID		"PCI:1:5:0"
EndSection

**_Server layout_**

Section "ServerLayout"
	**Option		"AIGLX"       "true"**
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

**_and i added this section_**


[B]Section "Extensions"
	Option "Composite" "Enable"
Endsection
[/B]

some of these may help you 
(on my laptop case my "Graphics by ATI Mobility Radeon 9000")

---

