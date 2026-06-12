---
title: "Adding Screen Resolutions"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by slipk487 on 2006-04-08
how do i add Screen Resolutions to the xorg

---

### Post by taurus on 2006-04-08
Well, you can either edit /etc/X11/xorg.conf by hand (using sudo) or you can run dpkg-reconfigure to generate a new /etc/X11/xorg.conf...
```

sudo nano /etc/X11/xorg.conf <-- to edit it...
-or-
sudo dpkg-reconfigure xserver-xorg <-- to reconfiguire it..

```

---

### Post by IYY on 2006-04-08
To open your xorg.conf file in an editor (in a terminal):

```
sudo nano /etc/X11/xorg.conf
```

Then find the section "Screen". There you'll see something like this:

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. 3D Rage Pro AGP 1X/2X"
        Monitor         "COMPAQ V500"
        DefaultDepth    16      
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection

```

You may have more than one possible depth. If you want, you can just make the changes to the depth that is set as default.

See the list of resolutions? 

```
"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
```

Just add your new res in there, in the same format.

---

### Post by ch604 on 2006-11-27
alright, let's say i added the resolutions i want into xorg.conf, but they aren't showing up in the drop down box in x. what should i do now?

the funny thing is, i added some other test resolutions later (800x600, etc) and they showed up and could be selected through the resolution menu. could it be that the resolution i'm trying to add is widescreen (1280x800)?

running an hp dv6103nr btw.

---

### Post by nickburns on 2006-11-27
You may need to do some research and figure out what the refresh rates are on your monitor and change the values in your /etc/X11/xorg.conf file.

I had the same problem and I had to change my values to a higher value

---

### Post by nickburns on 2006-11-27
something like

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-64
VertRefresh 43-60
EndSection

---

### Post by ch604 on 2006-11-28
well, i tried changing the refrech and sync numbers to insane numbers (1-200) and the options remain the same. This is what i have in my xorg.conf:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-50
	VertRefresh	43-75
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

and this is what is shown in the drop down menus:

Resolution: 1024x768, 800x600, 640x480
Refresh Rate: 60Hz

is there some other file im forgetting to configure?

---

### Post by twrock on 2006-11-28
Did you restart X?

---

### Post by ch604 on 2006-11-28
many times.

---

### Post by twrock on 2006-11-28
Sorry, but then I have no idea. All I had to do was exactly what it looks like you already did: add the resolution you want to the beginning of each line in the xorg.conf file and restart X. Well, I hope someone's got an answer for you.

(If I were discussing a Windows machine with someone, I'd ask about their video card driver at this point. Does it support the resolution they are trying to use? But since I'm only a noob to Linux, I don't know if that question is even meaningful to ask.)

---

### Post by twrock on 2006-11-28
One more thing. Check out the "Similar threads" section at the bottom of this page. Maybe something there will help.

---

### Post by CatKiller on 2006-11-28
It is meaningful to need information about the graphics device. We don't have that information, and apparently, neither does X: > Device		"Generic Video Card" A quick google suggests that that laptop has integrated Intel graphics, so if it isn't already set like it, you might try "**i810**" as the Driver in the Device section. I don't know for sure that that driver will work for your graphics chip - you probably have to look around. The "**vesa**" driver won't do the resolution you want.

Also, you might need to use a program called 915resolution. I've not used it, but it might help.

---

### Post by ch604 on 2006-11-28
the driver was set to i810 by default, but 915resolution did the trick. a little google and im all set, thanks guys!

---

