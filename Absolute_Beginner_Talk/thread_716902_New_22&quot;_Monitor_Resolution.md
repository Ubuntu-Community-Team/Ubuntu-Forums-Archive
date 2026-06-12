---
title: "New 22&quot; Monitor Resolution"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by gspaulding on 2008-03-06
When I installed Gutsy I had a 17" crt with an ATI X1600pro card.  Got the advanced desktop effects working, wobbly windows, cube, etc. using restricted driver.  Monitor died and I replaced with a Samsung 22" widescreen lcd, native resolution 1680 X 1050 (16:10 ratio).  The closest resolution available in Screen Resolution Preferences is 1280 X 720 (16:9 ratio).

How can I make the native 1680 X 1050 resolution available for this monitor?

---

### Post by wolfen69 on 2008-03-06
try doing in terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
if your video card is older, you may not be able run the resolution you want.

---

### Post by stchman on 2008-03-06
> **gspaulding said:**
> When I installed Gutsy I had a 17" crt with an ATI X1600pro card.  Got the advanced desktop effects working, wobbly windows, cube, etc. using restricted driver.  Monitor died and I replaced with a Samsung 22" widescreen lcd, native resolution 1680 X 1050 (16:10 ratio).  The closest resolution available in Screen Resolution Preferences is 1280 X 720 (16:9 ratio).

How can I make the native 1680 X 1050 resolution available for this monitor?

You need to edit your xorg.conf file.  Add the following in the line of resolutions towards the bottom of the file.

```
"1680x1050"
```

Remember to add that in ALL the lines that have resolutions in quotes.  Don't forget the quotes.

Your xorg.conf is located in /etc/X11/ folder.

I bought a new 24 LCD and it worked for me.

Hope this helps.

---

### Post by gspaulding on 2008-03-06
Thanks Wolfen69,
Which xserver driver do I select from the list?  My Screens & Graphics Preferences shows 

Graphics Card (ATI radeon (fbdev)
driver: fglrx

Graphics Card (Vesa driver (generic)
driver: vesa - generic vesa compliant video cards

I find ATI, fglrx, and fbdev in the list when running the code you provided.

My video card supports the 1680 X 1050 beautifully in windows.

---

### Post by gspaulding on 2008-03-06
Thanks stchman,
Obviously a newb, when I edit the file, I cannot save it.  I copied the file and edited it, but could not replace the original.  How do I get the edited file to replace the original?

Also, my old monitor is listed in the file.  Is that an issue?

---

### Post by deadmnky on 2008-03-06
i think you want the fglrx driver vesa i think was the default for mine and i had to install the other driver to get advanced desktop effects

---

### Post by stchman on 2008-03-06
> **gspaulding said:**
> Thanks stchman,
Obviously a newb, when I edit the file, I cannot save it.  I copied the file and edited it, but could not replace the original.  How do I get the edited file to replace the original?

Also, my old monitor is listed in the file.  Is that an issue?

The xorg.conf file is owned by root so you will need sudo.

```
sudo gedit /etc/X11/xorg.conf
```

Then make the corrections.  After that restart the workspace via CTRL-ALT-BKSP.

---

### Post by gspaulding on 2008-03-06
Thanks stchman,

I edited the file and first used a capital X in the "1680X1050".  When I re-edited and used the small "x" the resolution was available and it works great.  I really appreciate your help and thanks also to the other posters who offered suggestions.

---

### Post by nexnicholai on 2008-03-07
Hi, Im trying to get a Samsung Syncmaster 226BW to work with an ATI X1950 on gnome.

I tried the solution above and it almost works. There is a strip of screen on the right that isn't being rendered correctly.

Here is some of my xorg.conf, the only thing I added was the "1680x1050" in the Screen section.

```

Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"ati"
	Busid		"PCI:3:0:0"
	Driver		"fglrx"
	Screen	0
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes	"1680x1050"	"1600x1200@60"	"1600x1200@65"	"1400x1050@60"	"1280x960@75"	"1280x1024@60"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection


```

Attached is a screenshot of my desktop. Its not as obvious in the pic, but notice how the lines go straight on the right side of the picture. This is the area that is not being rendered.

Any help would be greatly appreciated.

-nex

---

