---
title: "Hi! Edgy Eft won't install on 3 different eMacs"
date: 2007-06-15
forum: Apple PPC Users
---

### Post by Dee Eon on 2007-06-15
Hello everyone!

I hope I'm posting in the correct forum! If not, pardons and please redirect me!

We have a problem in Boulder. Ubuntu Edgy Eft 6.10 won't install on 3 different eMacs here at the college library while the very same disks do successfully boot on several student iMacs. Our eMacs are 2004 1.25mgz G4 models with 512meg memory each.

We did everything in the documents and requirements but every time it runs the screen turns black then displays a colorful banner about "X-Server" not installed and color devices missing. I really don't understand it.

We're trying to give library customers a wide range of computer experiences and would like to include Ubuntu in the mix.

Can anyone help us?

Dee

---

### Post by pxwpxw on 2007-06-15
emacs and imacs have different graphics specs. 
 One thread that might help you to get the emacs screens going is
 
 Getting Started with a 700MHz eMac:

 [http://ubuntuforums.org/showthread.php?t=468671&highlight=emac](http://ubuntuforums.org/showthread.php?t=468671&highlight=emac)

 There are some othes in this forum that  may also help  if you search for "emac"

---

### Post by Auria on 2007-06-15
as for my eMac, i had to 'sudo dpkg-reconfigure xserver-xorg' and change screen type from 'imac' to 'emac'

---

### Post by pxwpxw on 2007-06-15
**Auria**

Is that all you had to do? Some others had to change horiz and vert settings?

---

### Post by Auria on 2007-06-15
> **pxwpxw said:**
> **Auria**

Is that all you had to do? Some others had to change horiz and vert settings?

yes, that was all.

but i can't confirm it would work with all eMacs.

---

### Post by coupdetard on 2007-06-17
> **Auria said:**
> yes, that was all.

but i can't confirm it would work with all eMacs.

I can confirm that that will not work with all eMacs. I tried it on my 700MHz and there was no such luck. I had to change the horiz and vert settings. These eMacs are running a different graphics chipset than mine, ATI Radeon 9200 AGP (much newer and better supported). However the CRT displays that are used in all of the eMacs, as far as I can tell, are the same. So manually changing to the horiz and vert refresh rates should fix it. Just make sure that you are using the default ATI drivers. Your xorg.conf file should have something like this in the sections I'm putting up here:

```

...
Section "Device"
	**Identifier	"ATI Radeon 9200"**
	**Driver		"ati"**
	BusID		"PCI:0:16:0"
EndSection

Section "Monitor"
	**Identifier	"eMac"**
	Option		"DPMS"
	**HorizSync	71-73**
	**VertRefresh	70-140**
	**Modeline "1280x960" 122.24 1280 1328 1424 1696  960 961 964 1002 +Hsync +Vsync**
	**Modeline "1024x768"  99.19  1024 1072 1168 1376  768 769 772 810  +HSync +Vsync**
EndSection

Section "Screen"
	**Identifier	"eMac Screen Settings"**
	**Device		"ATI Radeon 9200"**
	**Monitor		"eMac"**
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		**Modes		"1280x960" "1024x768"**
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	**Screen		"eMac Screen Settings"**
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection
...

```

The lines in bold above are the ones that you should be sure to check for modification/addition. The other display modes that are there can be added for completeness but unless you plan to be running at less than 24 bit color I wouldn't worry about it. I'm just anal. So I hope this helps.

---

