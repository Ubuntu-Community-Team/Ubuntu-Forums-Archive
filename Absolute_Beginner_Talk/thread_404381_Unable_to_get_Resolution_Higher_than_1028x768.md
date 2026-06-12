---
title: "Unable to get Resolution Higher than 1028x768"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by garius on 2007-04-08
I've just installed Ubuntu for the first time on my laptop and as well as the wireless issues i've got (which are currently being worked on in another thread) my only other major issue is that i seem unable to get any resolution higher than 1024x768.

Basically the situation is as follows:

**Problem:** Setting resolution above 1024x768 causes display to become blocky and fragmented (can provide screenshot if useful).

**Setup:** I'm running an ATI Radeon Mobility 9000 using the drivers that Fiery defaulted to for this card.

Now from browsing on here it seems that if 3D is required, i need to look into **fglrx**. But my initial concern is with getting a screen resolution that makes my laptop look a bit less like a slightly-more-advanced "speak and spell."

via the terminal i can see:

 ```
lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 01)
```

so my initial questions are:

1) is this correct?
2) if so, is this the correct version of the driver to be using (as far as people are aware)

and:

3) am i barking up completely the wrong tree here and not even looking in the right place?

Many thanks,

G

---

### Post by heimo on 2007-04-08
Check if you xorg.conf (configuration file for Xorg) has a device section (near the end of the file) which has line "Driver" with ati or radeon?
```
gksudo gedit /etc/X11/xorg.conf
```Could you also tell us what's the make and model of you monitor, and post your Monitor section, Screen section and the Device section between (EDIT: or nearby) them. For me (with nvidia card and 19" CRT) these look like (yours is and should be different):
```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 90.0
    VertRefresh     43.0 - 105.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nv"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    16
#    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       16
        Modes      "1400x1050" "1600x1200" "1920x1200"
    EndSubSection
EndSection
```

---

### Post by garius on 2007-04-08
sure - i get:

```
Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection
```

and then beneath that:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
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

---

### Post by heimo on 2007-04-08
You should probably follow steps over here to rerun "dpkg-reconfigure xserver-xorg"
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Your config doesn't show any resolutions higher than 1024x768 and also your monitors settings seem quite low (but these depend on the actual make and model of the monitor).

---

### Post by garius on 2007-04-08
**heimo** you are an absolute bloody star. If you are ever in Brighton, England and in need of a pint then give me a shout because i definitely owe you one. :)

i now have a far more human-readable (although apparently not "girlfriend readable", going by the moans) 1600x1200 resolution refreshing at 60hz.

for the record i did this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg
```

then at the resulting screen let it autodetect as much as possible, but:

1) manually selected ATI
2) manually specified ATI RADEON R250
3) manually specified the available/optimum resolutions

i left the monitor make etc as "generic" and did a "medium" selection on the specifications - which allowed me to chose which resolutions i knew the monitor to be capable of, rather than the "advanced" which requires the vertical and horizontal rates etc.

I then did a ctrl+alt+backspace restart.

---

### Post by heimo on 2007-04-08
Excellent that you got it working! Now I'll need to add Brighton on a list of places to visit. :D

---

