---
title: "unable to save x"
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by durableapostle on 2006-05-20
I am trying to change my screen resolution to a larger size.

Here's my problem:

I go through the process of backing up my "stuff" (/etc/X11/xorg.conf /etc/X11/xorg.conf.bak). I then reboot, and my screen stays the same. When I check the "new" /etc/X11/xorg.conf, it is exactly as it was before.

When rebooting, I am reversing the process above (/etc/X11/xorg.conf.bak /etc/X11/xorg.conf), then startx.

Obviously, I'm doing something wrong--probably something simple--but hey, I'm a complete n00b here, more than words can say....

Any suggestions?

---

### Post by macdo on 2006-05-20
What are you trying to change in xorg.conf?

---

### Post by adam.tropics on 2006-05-20
Go to a terminal, type

sudo dpkg-reconfigure xserver-xorg

<enter password>

Follow it through, selecting the correct driver (but other than that it tends to use default values that at least work well enough to get you started)

and presto...............with luck anyway!!

Can't be more helpful without your posting more information, video card etc etc....

---

### Post by durableapostle on 2006-05-20
I tried to re detect the monitor--no change.

What I'm trying to do is adjust my screen resolution.  I've tried all of the common places.

I've made changes to X, but they NEVER save.  NEVER!  When I reboot, it is as if I never made any changes to the horz and vert, or depth, or resolution.

I'm not sure why it won't save.  Here's what ia have:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection


Notice that I have no horz and vert values listed in monitor....  When i change it (and save, then reboot), it goes back to this every time.  My changes are not saved.

I'm pulling my hair out here....

---

### Post by bluevoodoo1 on 2006-05-20
Maybe some more information might be found here...
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

if you have your monitor's manual or its model number, perhaps you can find the sync rates?

---

### Post by macdo on 2006-05-21
You wouldn't have  a Dell monitor, would you?

Get your monitor make and model, and google for a manual, if you don't have yours.

Then get the sync rates, and do the whole dpkg-reconfigure thing, as shown above. When you get to the screen bit, go advanced, and enter the rates you picked up. 
That's what solved it for me in Breezy.

You might want to consider trying Dapper, if that doesn't resolve your problem. Put in a live cd, and see if it starts up with the proper resolution.

---

### Post by durableapostle on 2006-05-21
It is a Dell....

I've followed all of the above information, with no changes.  It's making me crazy.

Any other suggestions?

---

### Post by macdo on 2006-05-21
Dells are the only screens I've ever heard of that actively dislike Linux. I know, because I use one...

Here's the relevant section of my Xorg.conf file: see if anything in that helps you.
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL E771a"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9200 SE (RV280)"
	Monitor		"DELL E771a"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

These are the values that I had to input into the relevant part of dpkg-reconfigure:

Horizontal scan range  	31 kHz to 70 kHz 
Vertical scan range 	50 Hz to 160 Hz 
Optimal preset resolution 	1024 x 768 at 75 Hz

This for a Dell E771a monitor - if you have a different model, do a google search for the technical specifications to find what you need.

---

