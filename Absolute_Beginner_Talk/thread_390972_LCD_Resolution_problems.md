---
title: "LCD Resolution problems"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by benthegreat1 on 2007-03-22
Hello all,
  I'm new to Ubunto and am having problems getting the resolution to go any higher on my ViewSonic VA1912w screen. The highest i can set it to is 1280x1024, but the native resolution is 1440x900, and it will only work in Analog, I have had this problem running Fedora Core 6 with the Gnome desktop, and it has been no problem with Mepis under KDE.
I have also not been able to get my graphics card to work correctly, as you can see in my xorg.conf file.

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"VA1912w-3"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"VA1912w-3"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
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

My system is an AMD 64 3700+
Ati Radeon X1600XT
2048 Corsair Ram
Ubuntu 6.06LTS 64-bit
etc...

Thanks in advance

---

### Post by Kobalt on 2007-03-22
It seems you haven't installed the drivers for your graphic card.
I would recommend you to do that first...
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/graphics-cards.html)

---

### Post by benthegreat1 on 2007-03-22
Thanks for the reply, I have tried before to install the drivers for my graphics card, and have just tried again, but when i try to configure it it comes up with an error about not recognising my card, and I follow the prompts and enter the data myself, and when i reboot i only get a black screen. After spending hours in recovery mode, searching for help with lynx I finally gave up and reinstalled ubuntu.
Is there something I'm doing wrong or are my parts conflicting or something. Please help as I love Ubuntu and dont want to revert to Mepis (which is also cool, but not as cool)
Thanks again

---

### Post by cowlip on 2007-03-22
Could be this bug: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/67369](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/67369)

---

### Post by benthegreat1 on 2007-03-22
Thanks fot the link, I tried the ddcprobe that they recomended, but it returned the right resolutions, and i tried their fix as well, but i still cant select the right resolution.
Any other ideas.

---

### Post by benthegreat1 on 2007-03-23
Is the problem to do with the Gnome desktop, would it work with the KDE desktop, I like the gnome desktop better, but I can make sacrifices.

---

### Post by benthegreat1 on 2007-03-23
I have managed to get my resolution to the correct 1440x900 by installing some c librarys and stuff through synaptic, but 3D acceleration is still not working, fglrx is installed using the drivers from the ati site and to me the xorg.conf file looks ok, any help would be greatly apreciated, Thank You.

> Section "Device"
	Identifier	"ATI RADEON X1600"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"VA1912w-3"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON X1600"
	Monitor		"VA1912w-3"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
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

---

### Post by Corwin06 on 2007-03-24
I had the same bug. Had it in Windows too, found the way to correct it there.
(There needs to be some interface for Linux that's as flexible and powerful as the Windows Display Control Panel... Just saying that after playing for hours with xorg.conf)

For all of us with the Acer 1916W, that monitor stupidly scales down the 1440x900 VGA output to 1152x900, then scales it back up to 1440x900. That's why it refuses to auto-adjust right, when you confiigured the resolution right.

That bug was triggered when I replaced my 17" CRT with a dying 19" CRT (before I can afford to buy a second 1916W).
It did not appear at all when I was using the 17", or before.

I'm using TwinView for dual-monitor, so if you use Xinerama or an ATI card, it might not work.
From what I remember off the top of my head, the "iBook dual monitor setup" or something has instructions very simple, and they feel similar enough to TwinView that I think it should work too.

My workaround follows:

The idea is to have an output that will be scaled to 1440x 900 on the Acer. My experience in Windows had me find out that 1600x900 works well for that purpose.

Here follows the relevant section from my xorg.conf :
```

Section "Device"
	Identifier	"Generic Video Card"    # Asus 7600GS  Top Silent 
	Driver		"nvidia"  # Evil Binary Driver.
	BusID		"PCI:1:0:0"
	Option "MetaModes" "1440x900,1280x960;1024x768,1024x768"  #1440? no problem here
	Option "UseDisplayDevice" "CRT,CRT"  #Is this correct? The Acer is plugged in the VGA, because the DVI-out is the one that's considered the secondary display :confused: 
	Option "TwinView" "True" #Well, DUH
	Option "TwinViewOrientation" "RightOf"   # YMMV
	Option "AllowDDCCI" "True" #this was to try to solve a nvidia-settings bug
	Option "ModeValidation" "NoDFPNativeResolutionCheck"  #I don't think that's really needed
	Option "ModeValidation" "NoEdidModes" #because the CRT 19" is old and dying and VERY fuzzy above 1280x960
	Option "UseEdidFreqs" "True" #but I want my 1280x960 at at least the refresh rate the screen reports it can do (even though, like each every and all CRT ever, it reports one step below what it CAN do. But I'm not going to tweak THAT  *horrified look* )
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51 #both of
	VertRefresh	43-60 # these will be ignored
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"2880x960" "1600x900" "1280x960" "1024x768"   #AHA! This is important. 
		#That's the modes you will have available in the GNOME Screen Resolution thing. So, 
		#just calculate them : 1600 + <whatever your 2nd monitor needs>
		#and height <highest vertical res of both monitors>
	EndSubSection
EndSection

```


**THIS IS NOT PERFECT.** That quick hack works for me as of now. (It would not be a quick hack if I just cleaned up the conf to something more consistent...)
I'll post back here when I'll have my 2nd 1916W, if anything goes wrong.

---

### Post by benthegreat1 on 2007-03-24
Thanks for the great info, but I've managed to get everything sorted, my screen now looks great, and I have all my video drivers sorted, it was due to a few dependencys that needed updating, and im all smiles apart from I cant get cedega to work, i think its because it needs 32bit drivers or something.
:guitar: 
Anyway, Thanks all who helped.

---

