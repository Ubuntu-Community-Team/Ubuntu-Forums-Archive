---
title: "1440x900 resolution?? Cant boot with Samsung Synchmaster940bw?? Please HELP"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by harrington on 2006-12-28
I have posted about this and have been reading more into it. I really want to be able to try unbuntu. I read that my monitor . I cant boot, what happens is my monitor goes into standy or no signal just after watching it load. I hear the drums in the backround, I cannot press ctrl-alt+ anyF keys nothing happens. I amd just using the live cd, I want to try it and make sure it works before I install it. I have been looking everywhere for a clear answer to resolve this problem. Does this have to do with the fact that it is a very wide monitor, and the resolution ive heard is odd? Please help I dont know what to do next...

---

### Post by TuxCrafter on 2007-01-01
Just a quick fix for you:

use this a monitor section in your xorg.conf file

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1440x900" 106.50 1440 1520 1672 1904 900 903 909 934 -Hsync +Vsync
	DisplaySize 	381 238.13
	HorizSync	30-81
	VertRefresh	56-75
EndSection
```

And use this subsection in your Section "Screen" also in the xorg.conf file

```
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
```

---

### Post by ferg on 2007-01-01
Have a look at this... got my 940BW working great :)
 
[http://ubuntuforums.org/showthread.php?t=280683&highlight=samsung+940bw](http://ubuntuforums.org/showthread.php?t=280683&highlight=samsung+940bw)

---

