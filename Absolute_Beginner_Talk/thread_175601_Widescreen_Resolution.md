---
title: "Widescreen Resolution"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by Belathor on 2006-05-13
I'm using a Dell 2005 Widescreen monitor and Ubuntu didn't configure the resolution and refresh rate correctly. Screen Resolution in System --> Preferences tells me that the monitor is set at 1280 x 1024 @ 75hz and that is the highest it will go from there. It should be 1680 x 1050 @ 60hz. How can I change the resolution? Thanks!

---

### Post by oscar on 2006-05-13
you can change you settings in xorg.conf
It's probably good to make a backup:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
To edit
```
sudo gedit /etc/X11/xorg.conf
```
The sections you need to edit should be  at the bottom of the file
Refresh rates are are in the "Monitor" Section, make sure you have them correct before changing them.
Resolution settings are in the "Display" Subsection of "Screen", just follow the pattern set by the rest of the options.
Save, log out and restart X with Ctrl+Alt+Backspace and you should be able to change it.

---

### Post by Belathor on 2006-05-13
```
Section "Monitor"
	Identifier	"DELL D1626HT"
	Option		"DPMS"
```

Hi oscar,

That is what my Monitor section says? I don't see any refresh rates in there. :confused: 

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6200?]"
	Monitor		"DELL D1626HT"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "720x350" "640x480"
	EndSubSection
EndSection
```

That is what "dispay shows. How should I edit it for 1680x1050? 

Thanks for your help. :)

---

### Post by dsokus on 2006-05-13
[QUOTE=Belathor]
That is what "dispay shows. How should I edit it for 1680x1050? 

Thanks for your help. :)[/QUOTE]

I would delete all resolutions under all depths and add "1680x1050" instead of them all. And then pray that it works. :p Remember to have the backup...

---

### Post by physcsdrk on 2006-05-13
I believe that typing this: 

```
sudo dpkg-reconfigure xserver-xorg
```

and choosing all of the defaults except for what you want to change should work.

---

