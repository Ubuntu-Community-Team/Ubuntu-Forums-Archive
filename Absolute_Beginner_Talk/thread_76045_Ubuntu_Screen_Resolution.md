---
title: "Ubuntu Screen Resolution"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by lavarock09 on 2005-10-14
Hey Guys...

I want to change by ubuntu screen resolution to 1024 x 768 (or whatever it is)

It is also going to be connected to a widescreen TV...

The screen resolutions I have currently are '600x400', '800x600' & '832x624'

I have ran this code in Terminal 

'sudo dpkg-reconfigure xserver-xorg'

And it never works...

Please help me

---

### Post by Ampersand on 2005-10-14
You can add resolutions manually. Run

```
sudo gedit /etc/X11/xorg.conf
```

Towards the bottom, you'll find 'Section "Screen"'. In each subsection, add the resolutions of which your monitor is capable on the 'Modes' lines.

For example:

```

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

```

---

### Post by lavarock09 on 2005-10-14
This is what I've got

```

SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1200x800" "1152x864" "1024x768"
	EndSubSection
```

---

### Post by Qrk on 2005-10-14
I know you said that 

sudo dpkg-reconfigure xserver-xorg 

doesn't work, but make sure you have tried changing the driver from nv (or whatever) to vesa in the first dialog. That clears up a lot of problems.

---

### Post by lavarock09 on 2005-10-14
Why to vesa?

I'm using an ATI video card

---

