---
title: "Monitor problems"
date: 2010-07-07
forum: Apple Hardware Users
---

### Post by picabodaddy on 2010-07-07
This seems to be a common question in the forms, but I can't find an answer to my specific issue, and on my level of understanding.
First I'm ignorant of Linux on a whole.  I'm learning as I go.
Problem:
I have installed (successfully) Ubuntu 10.04 ppc on my powerpc g4 mac.  400mhz, 1g ram.  Its the blue model.  It works great, but it does not detect my monitor, and I can not change the settings past 800 X 600.  I am using a Dell 19 inch monitor.  Analog input (not DVI yet) resolution 12080 x 1024 60hz.

I believe I need to change the info in the xconfig file (but I don't know to what or how), and I may not be saying thta correctly.

Please help, thanks.

---

### Post by linuxopjemac on 2010-07-07
provide me with the specs of your monitor (link) and a full desription of your G4 (give link in everymac.com).

---

### Post by picabodaddy on 2010-07-07
The mac is [http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_400_agp.html](http://www.everymac.com/systems/apple/powermac_g4/stats/powermac_g4_400_agp.html)

The monitor is [http://reviews.cnet.com/lcd-monitors/ultrasharp-1905fp-19-inch/4507-3174_7-31232074.html](http://reviews.cnet.com/lcd-monitors/ultrasharp-1905fp-19-inch/4507-3174_7-31232074.html)

---

### Post by linuxopjemac on 2010-07-07
ATI Rage 128 graphics card

Apple advertised that the Rage 128 can support "up to 1600 by 1200 pixel resolution at 32 bits per pixel (millions of colors) and up to 85-Hz refresh rate." The Rage 128 Pro can support up tp 1920 by 1200.

#  Max Resolution  1280 x 1024 / 75 Hz  
#  Max Sync Rate (V x H)  75 Hz x 80 KHz  

Resolution
	
Horizontal scan range 	30 kHz to 81 kHz (automatic)
Vertical scan range 	56 Hz to 76 Hz (automatic)
Optimal preset resolution 	1280 x 1024 at 60 Hz
Highest preset resolution 	1280 x 1024 at 75 Hz

Preset Display Modes
Display Mode 	Horizontal Frequency (kHz) 	Vertical Frequency (Hz) 	Pixel Clock (MHz) 	Sync Polarity (Horizontal/Vertical)
VESA, 720 x 400 	31.5 	70.0 	28.3 	-/+
VESA, 640 x 480 	31.5 	60.0 	25.2 	-/-
VESA, 640 x 480 	37.5 	75.0 	31.5 	-/-
VESA, 800 x 600 	37.9 	60.3 	49.5 	+/+
VESA, 800 x 600 	46.9 	75.0 	49.5 	+/+
VESA, 1024 x 768 	48.4 	60.0 	65.0 	-/-
VESA, 1024 x 768 	60.0 	75.0 	78.8 	+/+
VESA, 1152 x 864 	67.5 	75.0 	108 	+/+
VESA, 1280 x 1024 	64.0 	60.0 	135.0 	+/+
VESA, 1280 x 1024 	80.0 	75.0 	135.0 	+/+

ok...five me the output of:

```
cvt 1280 1024 75
cvt 1280 1024 60
cvt 1152 864
cvt 1024 864 75
cvt 1024 864 60
```

---

### Post by picabodaddy on 2010-07-07
cvt 1280 1024 75

# 1280x1024 74.90 Hz (CVT 1.31M4) hsync: 80.30 kHz; pclk: 138.75 MHz
Modeline "1280x1024_75.00"  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync

cvt 1280 1024 60

# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

cvt 1152 864

# 1152x864 59.96 Hz (CVT 1.00M3) hsync: 53.78 kHz; pclk: 81.75 MHz
Modeline "1152x864_60.00"   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync

cvt 1024 864 75

# 1024x864 74.75 Hz (CVT) hsync: 67.65 kHz; pclk: 92.00 MHz
Modeline "1024x864_75.00"   92.00  1024 1088 1192 1360  864 867 877 905 -hsync +vsync

cvt 1024 864 60

# 1024x864 59.93 Hz (CVT) hsync: 53.76 kHz; pclk: 72.25 MHz
Modeline "1024x864_60.00"   72.25  1024 1080 1184 1344  864 867 877 897 -hsync +vsync

---

### Post by linuxopjemac on 2010-07-07
Try this xorg.conf:
```

Section "Device"
	Identifier	"ATI"
	Driver		"ati"
	BusID		"PCI:0:16:0"
Option "NoInt10" "true"
EndSection

Section "Monitor"
	Identifier	"Standardmonitor"
	Option		"DPMS"
	HorizSync	30-81 
	VertRefresh	56-76
# 1280x1024 74.90 Hz (CVT 1.31M4) hsync: 80.30 kHz; pclk: 138.75 MHz
Modeline "1280x1024_75.00" 138.75 1280 1368 1504 1728 1024 1027 1034 1072 -hsync +vsync
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync
# 1152x864 59.96 Hz (CVT 1.00M3) hsync: 53.78 kHz; pclk: 81.75 MHz
Modeline "1152x864_60.00" 81.75 1152 1216 1336 1520 864 867 871 897 -hsync +vsync
# 1024x864 74.75 Hz (CVT) hsync: 67.65 kHz; pclk: 92.00 MHz
Modeline "1024x864_75.00" 92.00 1024 1088 1192 1360 864 867 877 905 -hsync +vsync
# 1024x864 59.93 Hz (CVT) hsync: 53.76 kHz; pclk: 72.25 MHz
Modeline "1024x864_60.00" 72.25 1024 1080 1184 1344 864 867 877 897 -hsync +vsync 
Option "PreferredMode" "1280x1024_75.00"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI"
	Monitor		"Standardmonitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x864"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x864"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x864"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x864"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x864"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x864"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by picabodaddy on 2010-07-07
Just xorg.conf into the terminal, and paste?

Sorry I'm very new.

---

### Post by linuxopjemac on 2010-07-07
I made it easy for you:

```
wget http://mac.linux.be/files/xorg.conf
sudo mv xorg.conf /etc/X11/xorg.conf
```

Reboot and hopefully you have a working Ubuntu machine.

---

### Post by picabodaddy on 2010-07-08
Worked like a champ.  Thank you very much.  Just for info sake: what you did was change the file, had me download it and them move it to replace the old file, correct?

---

### Post by linuxopjemac on 2010-07-08
> worked like a champ. Thank you very much. Just for info sake: What you did was change the file, had me download it and them move it to replace the old file, correct?

yep

---

### Post by Goolie on 2010-07-08
> **linuxopjemac said:**
> yep

just a "yep" what a bad-@$$ 

if I ever have a problem I'll know who to PM

:p

---

### Post by linuxopjemac on 2010-07-08
Only post if you have something to contribute. I don't like swearing.

---

### Post by christopher1919 on 2012-11-08
The solution here worked for me too on a G4 with Debian Wheezy and the Xfce desktop. I'm adding this because I had endless problems with the screen resolution being stuck 800x600 on a Packard Bell Viseo 230.

Having been through just about every possibility (or so I thought) with wrong advice about xrandr and what to put in the conf file, this is the solution *that actually worked*.

Thankyou to linuxopjemac for:
wget [http://mac.linux.be/files/xorg.conf](http://mac.linux.be/files/xorg.conf)
sudo mv xorg.conf /etc/X11/xorg.conf
Now, if only I could get this thing to recognise the Norwegian keyboard layout...

Thankyou Ubuntu forums!:P

---

### Post by CaloCuervo on 2012-11-11
This is not a reply but a plead for help.  I migrated from 12.04 to 12.10 (IMac G5 PPC, NVIDIA Geoforce FX5200 graphics card), after the update I cannot see any text or logos on my display.  However, the wallpaper (a family photo) displays as it was with 12.04.

I am assuming is that is the Xorg file, but how can I edit the file if I cannot see what I'm typing?

Thanks
Claudio

---

