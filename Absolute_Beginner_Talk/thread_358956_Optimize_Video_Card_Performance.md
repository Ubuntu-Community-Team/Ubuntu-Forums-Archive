---
title: "Optimize Video Card Performance?"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by Darko Beta on 2007-02-11
I'm trying to get my Ubuntu to be a little more responsive--from reading forum posts and other information it seems like it should be faster.

I am running a P4 1.8ghz with 1gb of ram and Windows XP is very snappy.

Right now, when I switch between apps, or the desktop, it takes a second or so to draw the screen and scrolling is somewhat of a chore on any app.  I have mouse gesture trails activated in Swiftfox and the trails can't keep up with the mouse!  I have resorted to booting XFCE sometimes because it's a relief, but again, it doesn't seem like this should be necessary on my rig.

I have an ATI 9550.  I followed numerous posts to get drivers installed and failed about six times before I got direct rendering to work.  Eventually, I did get Beryl running--but it is terrible slow and I only run it for fun on occasion.  I'm wondering if my xorg settings are set up in a bad way because I have fiddled around in there so much.

Does anyone have any suggestions for how I might be able to improve the responsiveness of my setup?  Would it benefit me to just buy a $60 nvidia card and switch out the ATI?

```
Section "Device"
	Identifier	"ATI Radeon 9550"
	Driver "radeon"
	Option "DRI" "true"
	Option "ColorTiling" "on"
	Option "EnablePageFlip" "true"
	Option "AccelMethod" "EXA"
	Option "XAANoOffscreenPixmaps"
	Option "RenderAccel" "true"
	#Option "AGPMode" "x" <- x may be 2 or 4 depending on your system
	Option "AGPFastWrite" "on"
	EndSection

Section "Monitor"
	Identifier	"Samsung 730B"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon 9550"
	Monitor		"Samsung 730B"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

---

### Post by Patrick K on 2007-02-11
Not a video solution but you could try reducing swappiness. That is the tendency to use the swap partition. Here is a page on it:
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Swappiness_.282.6_kernels.29](http://gentoo-wiki.com/FAQ_Linux_Memory_Management#Swappiness_.282.6_kernels.29)
I set mine at 20, default is 60. A higher number increases swappiness. With a gig of memory it might not make much difference. 

Also, is DMA enabled for your drives?

---

### Post by Darko Beta on 2007-02-11
I'll try changing the swappiness.  I have another thread open about changing disk settings.  DMA is on, but there is an error preventing me from changing any of the other settings that might improve performance:

[http://www.ubuntuforums.org/showthread.php?t=358248](http://www.ubuntuforums.org/showthread.php?t=358248)

---

### Post by Darko Beta on 2007-02-12
If someone could at least confirm that my xorg looks normal, I would appreciate it.  Just trying to make sure I'm not missing something that could stop things from having to draw on the screen for a second every time I switch apps.

---

### Post by Patrick K on 2007-02-12
I know nothing about ATI cards and little about Linux so take this as such.

I would comment out all the options for the card and see what happens. Then I'd uncomment them one at a time. It could be one or more of the options are slowing down the screen. This is more of a guess than anything else. Perhaps some combination of options are conflicting. 

Nothing jumps out that looks wrong to me, but I'm not an expert. 

As for the drive setting, I change a number of them to what should be higher performance settings but the drive actually got slower. I went back to the default setting since they gave the highest speed.

---

