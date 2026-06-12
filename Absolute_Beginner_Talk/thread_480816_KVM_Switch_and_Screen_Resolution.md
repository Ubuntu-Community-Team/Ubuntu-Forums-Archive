---
title: "KVM Switch and Screen Resolution"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by MPH on 2007-06-21
I am using a KVM switch between a Feisty PC and a Windows PC.  Unless the Feisty PC is switched to the monitor while booting, the screen resolution is limited to a max of 800x600.  When Windows ran with the same hardware, it didn't auto-detect the monitor's capabilites each time it booted so the screen resolution wasn't restricted.

Is there a way to configure Feisty once and save it such that it doesn't need to auto-detect the monitor each time it boots?

---

### Post by h0ax on 2007-06-21
You will want to set up the monitor in your xorg.conf with the resolution you prefer.
that's located in /etc/X11/xorg.conf

sudo gedit /etc/X11/xorg.conf

look for "Monitor" and "Screen" sections -- this is where you would set it up properly.

Make backups of your xorg in case you break something though
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkup

---

### Post by MPH on 2007-07-02
**Here are the "Monitor" and "Screen" sections.  It's not obvious what to change to fix the problem I stated in my original post...**

Section "**Monitor**"
	Identifier	"PS790-2"
	Option		"DPMS"
EndSection

Section "**Screen**"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage 128 Pro Ultra TF"
	Monitor		"PS790-2"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

### Post by doozy on 2007-07-15
Did you get this resolved, as I have the same issue with a KVM attached.

My screen is recognised correctly (Xerox XM3-19w) in the file mentioned above, but I only get the lowest resolution (640x480) choice in Windows Scree Resolution settings.

Works ok without the KVM inline.

Thanks

Section "Monitor"
	Identifier	"XM3-19w"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"XM3-19w"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1440x1440" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x1440" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x1440" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x1440" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x1440" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x1440" "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

### Post by Wim Sturkenboom on 2007-07-15
Add *HorizSync* and *VertRefresh* values to the monitor section. Tthe system is not able to determine these values (as the KVM switch probably does not pass them).

example:
```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       27.0 - 96.0
        VertRefresh     50 - 160
EndSection
```

You can find the values to be used in your monitor's manual.

---

### Post by MPH on 2007-07-15
[SIZE="7"]Fantastic!!!!![/SIZE]  [SIZE="5"]Thank you, Wim!!![/SIZE]

I added the **HorizSync** and **VertRefresh** lines... along with the ranges of values for my monitor I found in the monitor's manual... and the screen resolution settings work perfectly now, even _without_ the KVM switch set to my Ubuntu PC!

:guitar:  [SIZE="5"]That Rocks![/SIZE]

---

### Post by Wim Sturkenboom on 2007-07-16
Pleasure

---

