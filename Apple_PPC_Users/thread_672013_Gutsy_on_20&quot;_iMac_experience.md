---
title: "Gutsy on 20&quot; iMac experience"
date: 2008-01-19
forum: Apple PPC Users
---

### Post by stream303 on 2008-01-19
I just installed Gutsy on my late 2004 1.8 gHz 20" iMac with nvidia (nv) driver and thought I'd share the experience.

This model was purchased with only bluetooth and NO wireless.

Installation with Alternate text-based iso:

Like an earlier install of Ubuntu, the fans screamed, although the air was cool.  Once installed with Gutsy, the fans calmed down thank goodness.

Everything seems to work ok, although the X11 screen is shifted just a bit to the right, and had to manually set up my wired ethernet by playing around with the Network Manager applet.

UPDATE FEB 2008:  The screen-shift problem was fixed by using the **nv_drv.so** file from a working Feisty installation, and copying it into /usr/lib/xorg/modules/driver in the Gutsy install.

I had to manually turn on subpixel font smoothing in system > preferences > appearance > fonts.
To make it a bit easier on my eyes I increased the dpi to 100 dpi found under font details.

The nvidia card can further sharpen very small fonts.  I edited the **/etc/X11/xorg.conf** file with the "FPDither" "true" option:

```
Section "Device"
	Identifier	"nVidia Corporation NV34M [GeForce FX Go5200]"
	Driver		"nv"
	BusID		"PCI:240:16:0"
	**Option		"FPDither" "true"**
EndSection

```

Nice and sharp.  Off to find a cure for brightness and display shifting, but otherwise, I'm very happy.

The video shifting to the right is a little bit bothersome, but not unusable.  I just use a solid dark background and manually stretch my apps out instead of letting them go full screen.  I looked at XVIDTUNE to see if I could get a modeline to move the display, but nothing is moving it.  I can live with it for the time being.

The display is pretty bright, and I can't find a way to tone it down a bit.  As long as I don't look at a paper-white background in a darkened room, it may be ok.

Out of the box sound worked, frequency scaling worked, and no screaming fans.   I think I'll be putting OSX on the shelf even with these small issues.

Also got rid of that annoying Apple "bong" on startup.  Just run this once in the terminal:
```
sudo nvsetvol 0
```

---

