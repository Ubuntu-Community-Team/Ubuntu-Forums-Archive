---
title: "Feisty Live CD resolution question"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by mjpatey on 2007-01-16
Hello, group!

I haven't been here in quite a while.  I already have a Dapper install, and have just burned the ISO of the latest Feisty offering.

I'm trying to see how much I can tweak in Live CD mode, but can't seem to get Live Feisty to display my LCD monitor's native resolution (1200x1024).

It's been a while since I've had to make this kind of tweak, so please bear with me... I tried adding the resolution to the list in xorg.conf, logging off and back on again.  Though what I added does indeed appear in xorg.conf even after logoff and logon, I still don't get the option to use the new resolution I added.

I honestly have no idea if this is the right sort of thing to do or not, just going on instinct and vague recollection.

Here's the section of xorg.conf that I modified:

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1200x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1200x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1200x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1200x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1200x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1200x1024" "1024x768" "800x600" "640x480"
	EndSubSection

In each line listing "Modes" I added the "1200x1024" myself.

Obviously, that's not the thing to do, as I still only have the 3 resolutions that were listed automatically.  Is there a tweak that will allow me to view 1200x1024 using the Live CD, or will this sort of thing only work with a true install?

Thanks for any help you may have!

-Mark

---

### Post by bodhi.zazen on 2007-01-16
Try adding your monitors horizontal and vertical refresh rates in the monitor section.

If you do not know them, check in your dapper xorg.conf

---

