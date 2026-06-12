---
title: "Changing the screen resolution on a Vaio FS550"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by Sunships on 2007-09-15
[RESOLVED - I installed Ubuntu 7.10 over my old 6.10 installation, and widescreen works great now :)]

Hi all,

I have been playing around with Ubuntu 6.10 for a little while now, and it works fine, but there are a few small things which would make life much better - I would like to change my screen settings to enable higher resolutions. 
I am using a Sony Vaio FS-550, and am currently restricted to 1024x768. Under System->Preferences->Screen Resolution I have the (apparent) option to choose 600x480, and 800x600, but selecting these doesn't have any effect. 

I have made some attempts to modify my xorg.conf file, based on solutions posted in other threads, and I have also tried the script available here:[http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html)

..but sadly with no effect either. After a few adventures with vi and without a GUI, I have managed to restore xorg.conf to a functional state, and have decided it is time to get help from someone who knows what they are doing! 

If anyone knows what specifically needs to be done to get an FS-550 to work at 1280x1024 in widescreen , please let me know! Here is the relevant section of my current xorg.conf:

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

I guess it needs something like:

```

Section "Monitor"
Identifier "Generic Monitor"
HorizSync 28.0 - 64.0
VertRefresh 43.0 - 60.0
Option "DPMS"
EndSection

```

...in there somewhere? I don't know what values I need to use, and suspect something else may be needed in addition to this to make things work. 

If you made it this far, thanks for reading! Hope someone out there knows what to do!

---

### Post by MrHippocampus on 2007-09-15
To do this on my 1280x800 laptop I borrowed the refresh rates from my 1280x1024 monitor,

```

Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    30 - 80
        VertRefresh  50 - 75
        Option       "DPMS"
EndSection

```

Although they go higher than needed for 1280x800 putting those numbers in worked.

---

### Post by Sunships on 2007-09-15
Thanks, I'll give them a try!

---

### Post by Sunships on 2007-09-15
Alright - I made the change to xorg.conf, and rebooted, but Screen Resolution still shows the original 3 resolutions.

---

### Post by MrHippocampus on 2007-09-15
Try having a look through /var/log/Xorg.0.log and see if you can see anything complaining about about the monitor resolution in there.

---

### Post by Sunships on 2007-09-16
> **MrHippocampus said:**
> Try having a look through /var/log/Xorg.0.log and see if you can see anything complaining about about the monitor resolution in there.

OK, I think I have found two things which might be relevant. Firstly, it doesn't seem to recognise 1280x800 as a valid mode:

```

(II) VESA(0): Generic Monitor: Using hsync range of 28.00-64.00 kHz
(II) VESA(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz
(II) VESA(0): Not using mode "1280x800" (no mode of this name)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (75, 75)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)

```


Above this, a lot of modes are listed with the following values:

```

Mode: 107 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0

```

0 for all entries is wrong, I guess? The only modes with non-zero values are those for 1024x600, 1024x768, 640x480, 800x600. Note that 1024x600 is not offered as a choice of resolution under System->Preferences->Screen Resolution..I don't know if this is significant.

I tried ```
915resolution -l
``` and none of the mode numbers listed appear in /var/log/Xorg.0.log

---

### Post by Sunships on 2007-09-16
*bump*

---

### Post by Sunships on 2007-09-16
*bump*

---

### Post by bubbalouie on 2007-09-16
If I recall correct there is a widescreen resolution fix for the 915 chipset. Have you:

**sudo apt-get install 915resolution** <-- My bad, you have already tried... sorry

I don't know if this will help, but here is the site and it mentions your model laptop:

[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

Here's an excerpt:
> 
**Using 915resolution from within an Xserver**
915resolution is going to be incorporated into the i810 driver from X.org. It should be in an upcoming release. This will void the need to run 915resolution manually. When I find out the appropriate X server has been released I'll put a notice on the website.

In the meantime, there is a test driver that has 915resolution built in here

The syntax to override a BIOS resolution is below. You place the option in the driver section.

Option "ForceBIOS" "1024x768=1400x1050"

This will re-program the old 1024x768 to become a new 1400x1050 one.


Other than the above, perhaps updating to a more recent Ubuntu may help. 7.04 is much better IMHO, and the last few weeks I have had only one issue with Gutsy (bad update which I fixed), which is small for the number of improvements (suspend working etc).

Anyway, best of luck :)

Ryan

---

### Post by Sunships on 2007-09-16
Alright, I tried resolution915. Things went a little funky, and I was taken back to the login screen, which was now widescreenified. Logging in to a normal GNOME session didn't work, just brought me back to the login screen again, but on starting an Xfce session I had wonderful 1280x800 widescreen goodness. Sadly, logging out made my PC crash, and although I can now log into GNOME, I am back at 1024x768 for everything. Also, during startup and shutdown the screen shows some crazy stuff, like two copies of the login splash screen above a load of scanlines (in nice purple and green).

I have no idea where to put the "force BIOS" line either. Does this go in Xorg.conf or one of the 915resolution files? If so, where?

---

### Post by bubbalouie on 2007-09-16
I imagine it would go in the xorg.conf file, in the section that describes the driver for the 915 chipset. The best thing to do would be to backup the xorg.conf and give it a try (boot into a recovery console to restore if things go awry). 

I had a similar issue with my media PC, however replacing my video card didn't address the issue, turned out that the VGA cable to my TV didn't include the digital lines to identify the display, consequently I never bothered to resolve my own intel issue as I had just thrown $100 down on a new video card.

In all honesty though, I really do recommend using a newer release, the current release even has the right resolution on the live disk (1280x800) for me, admittedly I have a geforce go, however, 6.10 never did that, I just got 1024x768.

---

### Post by Sunships on 2007-09-16
Thanks for the advice - I think I was mistaken with 1280x800, think it might be 1280x1024, and have been trying both. 

I modified xorg.conf as follows:

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Option		"ForceBIOS" "1024x768=1200x1024"
	HorizSync       30-96
     	VertRefresh     50-160
EndSection

```

...but with no effect at all. I have also tried all the applicable solutions listed here: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

but again with no effect. I will try a newer version liveCD then, and see how that works, but am loathe to re-install Ubuntu from scratch again... :s

---

### Post by Sunships on 2007-09-16
It seems that I have the same problem with 7.04 - it is just a little more "honest" in that it only shows the current resolution, and no others.

---

### Post by Sunships on 2007-09-16
*bump*

---

### Post by Sunships on 2007-09-16
*bump*

---

### Post by bubbalouie on 2007-09-16
Your xorg.conf file says 1200x1024, you described your resolution as 1280x1024, perhaps this may need addressing. However [Sony]("http://www.sonystyle.ca/commerce/servlet/ProductDetailDisplay?storeId=10001&langId=-1&catalogId=10001&productId=1001048") say you have a 1280x800 display, so I would work with that.

In the past when trying new operating systems I have made a ghost of a partition ahead of the change in case I made a big mistake. An install may help (able to properly load drivers and any changes you make), however, that is 30 minutes of your time, plus however long it takes to get all your favorite packages back into place.

Perhaps for now, if I were you I would try to force a change to 1280x800, if that fails, rinse and repeat for a newer distro. Sadly not having a widescreen intel 915 based laptop to verify with I can not help you much. Sorry

Good Luck.

Ryan

---

### Post by alienexplorers on 2007-09-16
Try adding a modeline to the monitor section of your xorg.conf file.
Example:
> Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Option		"ForceBIOS" "1024x768=1200x1024"
	HorizSync       30-96
     	VertRefresh     50-160
        [COLOR="Red"]# 1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
        Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync[/COLOR]
EndSection

---

### Post by Sunships on 2007-09-17
> **alienexplorers said:**
> Try adding a modeline to the monitor section of your xorg.conf file.
Example:

Thanks for your suggestion, but sadly, this did not work either. 

I have also tried making a "915resolution" file in etc/default/ as suggested in another thread, but with no effect.

---

### Post by bubbalouie on 2007-09-18
Too bad, I have had issues like this, they stopped me from completely switching, Gutsy, finally addressed my last two isues, suspend, and screen brightness, so I no longer run Windows, at all (except on my media PC, but I will fix this in a ffew weeks when I have time). 

Perhaps a Gutsy install will sort you out. Though reinstalling is drastic. Sadly I think right now I am as useful to you as a crow bar is when you are drowing.

Good luck and keep trying. :)

---

### Post by MrHippocampus on 2007-09-18
> **bubbalouie said:**
> Too bad, I have had issues like this, they stopped me from completely switching, Gutsy, finally addressed my last two isues, suspend, and screen brightness, so I no longer run Windows, at all (except on my media PC, but I will fix this in a ffew weeks when I have time). 

Perhaps a Gutsy install will sort you out. Though reinstalling is drastic. Sadly I think right now I am as useful to you as a crow bar is when you are drowing.

Good luck and keep trying. :)

Yeah, gusty ships with the new intel driver which is apparently much better than the previous intel ones.

---

### Post by Sunships on 2007-09-18
Thanks for your help Bubbalouie, MrHippocampus, and everyone else who stopped by to look. Guess I will take it easy until next month then - I'll wait until 7.10 is ready for general release. In the meantime I will play around in Xfce - I think I was quite close and a combination of the suggestions here might work out. 

Will post here if there are any further developments...

---

### Post by Sunships on 2007-10-19
Hi, I tried the live CD for Ubuntu 7.10, and widescreen worked fine. I installed it over my old 6.10 installation, and so far so good. Many thanks to everyone who took time to read and offer advice.

---

