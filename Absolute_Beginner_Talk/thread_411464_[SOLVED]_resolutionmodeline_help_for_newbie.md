---
title: "[SOLVED] resolution/modeline help for newbie"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by il-luzhin on 2007-04-16
New to ubuntu.  I have now spent six hours trying to get my screen to display in 1440x900 with zero success.  Having trouble finding a modeline for my viewsonic vx1945wm (1440x900 @ 60, 75 Hz)  Finding few modeline calculators have this option.

PLease help.  I'm not nearly linux enough to solve on my own since my xp laptop was stolen yesterday.  

but will the modeline even fix it?  :(

---

### Post by Browser_ice on 2007-04-16
I know the feeling. I changed my monitor 3 weeks ago. I discovered I had bigger resolutions with it. In Windows-XP it was easy to access them. But in Ubuntu, I had to search the docs, forums for 1 hour and then found out I had to change one file to ADD the new resolution. 

Having something so simple and so basic to do, I am surprise there are no easy/automatic way of doing it without spending more then 15 minutes trying to figure it out (for beginners).

**I would love to see an explanation on why this hasn't been made easier to do.**

As for helping you, I don't recall the exact file name as I am at the office now. I think its something like xorg.conf or xconf.org  . Look for something similar in the forum to find out how to change the resolution.

---

### Post by il-luzhin on 2007-04-16
I defintely found the command:

sudo gedit /etc/X11/xorg.config

but now that I have adjusted the monitor section (hsync, identifier, etc) everytime i change items in the screen section it either makes no change or crashes  x server.

I have zero programming experience and this is trial by fire for me.

---

### Post by Wim Sturkenboom on 2007-04-17
It will help if you post the sections device, monitor and screen of the X configuration file here and also tell us which videocard you're using.

Further you don't need to change your identifier (as it's just an identifier and nothing more). It usually causes more problems as you might forget to change it somewhere else in the config as well and next X does not want to start.

There is a command to configure it  (something *sudo dpkg-configure ....*) but I don't know if it always works. I've never used it as I'm reasonable comfortable with the X configuration file when it comes to video.

After setting up the refresh rates correctly, make sure that you have the correct driver for the video card (i.e. *vesa* and *nv* will more then likely not have the option to use 1440x900 resolution) if you have an nvidia card. Same for the *i810* driver if you have a more modern intel grpahcs chip. Not familiar with ATI, so can't say anything about it.

Next modify the default subsection (usually it's 24) of the screen section and add the new resolution (see bold in the example below)
```

    Subsection "Display"
        Depth       24
        Modes **"1440x900"** "1024x768" "800x600" "640x480"
    EndSubsection

```

If you still  have problems, post the requested info and error messages. You can find errors in /var/log/Xorg.0.log

PS
HorizSync 30 - 82
VertRefresh 50 - 85

---

### Post by il-luzhin on 2007-04-17
I think I'm okay with the xorg.config file.


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-82 
	VertRefresh	50-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

but I may be having a prob with drivers.  I'm using a tired old sis-730 with on board video card.  Haven't yet found updated driver for linux.

Any help is appreciated.

---

### Post by il-luzhin on 2007-04-17
i believe I have a new driver but don't know where to put it.

I have gotten xsis.rpm from [www.sis.com](www.sis.com) but now don't know where to extract it or how to install it.

---

### Post by Wim Sturkenboom on 2007-04-17
Although I might be wrong, I don't think that your (integrated) video card supports that resolution. According to [http://en.wikipedia.org/wiki/SiS_630/730](http://en.wikipedia.org/wiki/SiS_630/730) the board is from 1999 and I wonder if widescreen already existed in those days. And if the videocard does not support it, a newer driver will not make any difference.

But as said, I might be wrong.

// Edit: I think I wrong as it supports a resolution of 1920x1200

---

### Post by il-luzhin on 2007-04-17
Still nothing.  Any advice on how to install a downloaded driver?  Don't believe ubuntu has package for sis730.

modeline added.

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-82 
	VertRefresh	50-85
	**Modeline 	"1440x900@75" 146.10 1440 1472 2024 2056 900 917 928 946**
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by Zimmer on 2007-04-17
Have a look at post #3 here

[http://ubuntuforums.org/showthread.php?t=276650](http://ubuntuforums.org/showthread.php?t=276650)

and see if that helps you obtain a correct modeline statement for your hardware...
Edit/Delete Message

---

### Post by il-luzhin on 2007-04-17
I dropped a new driver XSiS_SVGA into /usr/X11R6/bin.  Can someone confirm that's the correct location because it has solved nothing.

Thanks Zimmer but I have 1440x900@75Htz modeline.

---

### Post by RedSquirrel on 2007-04-17
> **il-luzhin said:**
> I dropped a new driver XSiS_SVGA into /usr/X11R6/bin.  Can someone confirm that's the correct location because it has solved nothing.

Thanks Zimmer but I have 1440x900@75Htz modeline.


You're not actually using the Modeline, though. :)

You need to change your _Modes_ line to use the Modeline.

Change from this:

```
SubSection "Display"
        Depth        24
        Modes        [COLOR=Red]"1440x900"[/COLOR] "1024x768" "800x600" "640x480"
    EndSubSection
```to this:

```
     SubSection "Display"
        Depth        24
        Modes       [COLOR=Red]**"1440x900@75"**[/COLOR] "1024x768" "800x600" "640x480"
    EndSubSection
```

You might have trouble running a widescreen display with an old video card. I tried running 1440x900 with an old ATI card and it wouldn't work unless I used a line beneath the Modes line to specify the size of the virtual desktop:

```
     SubSection "Display"
         Depth        24
         Modes       [COLOR=Black]"1440x900@75" [/COLOR]"1024x768" "800x600" "640x480"
**         Virtual        1440 900**
    EndSubSection
```and even that didn't look very good, because I think it was just resizing 1024x768. I ended up exchanging the 1440x900 monitor for a 19" 1280x1024 monitor, a resolution I *knew* my video card would like.

Anyway, see if that change works. 

What did you do to install the driver? It's an rpm, for which I believe you need to use "alien". See [this]("http://www.psychocats.net/ubuntu/installingsoftware").

---

### Post by il-luzhin on 2007-04-19
that did it.  
Thnx

uhm...resolved?

---

### Post by dcstar on 2007-09-09
> **Wim Sturkenboom said:**
> Although I might be wrong, I don't think that your (integrated) video card supports that resolution. According to [http://en.wikipedia.org/wiki/SiS_630/730](http://en.wikipedia.org/wiki/SiS_630/730) the board is from 1999 and I wonder if widescreen already existed in those days. And if the videocard does not support it, a newer driver will not make any difference.
.......
There are some integrated SIS video cards that require a VBIOS upgrade to be able to display the 1440 x 900 resolution, the SIS website has a specific article explaining it: [http://www.sis.com/support/support_faqs_4.htm#73](http://www.sis.com/support/support_faqs_4.htm#73)

I used this procedure recently to upgrade a BIOS with a new SIS VBIOS that would support 1440 x 900, it may be of use to anyone else in the future who has this issue: [http://www.wimsbios.com/phpBB2/topic8989.html](http://www.wimsbios.com/phpBB2/topic8989.html)

---

