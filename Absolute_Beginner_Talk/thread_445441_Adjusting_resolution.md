---
title: "Adjusting resolution"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by gantww on 2007-05-15
Hello all,
I just wiped and reinstalled. Most devices seem to be working at the moment, but I can't get my resolution up over 640x480.

lspci indicated the following for my video card:
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)


Below is my xorg.conf (or just the screen-related part
------------------------------

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

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
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection


I'm running this on a Dell Inspiron 1100. I "think" the problem has to do with the missing HorizSync and VertRefresh settings, but I have no idea what to set them to. Any help would be very much appreciated.

Thanks,
Will

---

### Post by alienexplorers on 2007-05-15
You could delete 800x600 and 640x480.  Then do a ctrl+alt+backspace to see if it works.  What exact resolution are you looking for.  If it is not 1024x768 then delete that and pit in the resolution you are looking to use.

---

### Post by heimo on 2007-05-15
I didn't find correct kHz values in manual:
[http://support.dell.com/support/edocs/systems/ins5100/en/i1100-om.pdf](http://support.dell.com/support/edocs/systems/ins5100/en/i1100-om.pdf)

But it's a XGA display (1024x768) with regular 4:3 aspect ratio. I'd try something like:
```
HorizSync            40-55
VertRefresh          50-63

```

---

### Post by Kingsley on 2007-05-15
Going through this command might help.
```
sudo dpkg-reconfigure xserver-xorg
```

---

