---
title: "use a widescreen resolution?"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2006-10-23
I have a 17" widescreen screen on my laptop but only non widescreen resolutions are selectable. How do I change to widescreen resolutions and how do I figure out how large my max resolution is? (I think it is 1200x800)

---

### Post by TrinitronX on 2006-10-23
You may need to edit your xorg.conf file, located in : /etc/X11/xorg.conf

Add your target resolution as the first one after each "Modes" line in your "Screen" section.

For example, Mine is:
```
Section "Screen"
	Identifier "LCD Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "LCD Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     1
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

I simply added "1440x900" to the beginning of each "Modes" line under each display depth subsection under the main Screen section.  Make sure your "Monitor" and "Display" lines point to the correct entries in the cooresponding Monitor and Display sections that you wish to use.  (This refers to the name you have defined under "Identifier" for each of those sections).  Also make sure the "Identifier" you use for the screen is also listed under "Screen" line under your "ServerLayout" section.

---

### Post by dtown240 on 2006-10-28
These exact changes QUICKLY and EFFECTIVELY resolved my issue with an NVIDIA Ti4200 and a Viewsonic VA1912wb Series widescreen monitor.  Thank you!!!

> **TrinitronX said:**
> You may need to edit your xorg.conf file, located in : /etc/X11/xorg.conf

Add your target resolution as the first one after each "Modes" line in your "Screen" section.

For example, Mine is:
```
Section "Screen"
	Identifier "LCD Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "LCD Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     1
		Modes    "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

I simply added "1440x900" to the beginning of each "Modes" line under each display depth subsection under the main Screen section.  Make sure your "Monitor" and "Display" lines point to the correct entries in the cooresponding Monitor and Display sections that you wish to use.  (This refers to the name you have defined under "Identifier" for each of those sections).  Also make sure the "Identifier" you use for the screen is also listed under "Screen" line under your "ServerLayout" section.

---

### Post by jcrnan on 2006-10-28
Okey, so I checked my xorg and I only have 1200x800 as a resolution there, no others. Still, only 1024x678 and 800x600 and 640x400 shows up in the screen resolution window :(

Help?

---

