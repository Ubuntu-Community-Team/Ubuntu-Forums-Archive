---
title: "Another resolution problem"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by paul905 on 2008-04-05
I just added a new Acer flatpanel monitor to a new Gutsy install.

The ideal resolution for the monitor is 1440 x 900  (widescreen)

However it comes up in 1024 x 768 and the only options Screens & Graphics gives me is 3 lower ones.

The core of my xconfig looks like this:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Acer AL1716W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Acer AL1716W"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x1440" "1440x900" "1280x1280" "1280x1024" "1280x800" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


My (probably dumb) solution was to delete all the low resolution options. However when I restarted xserver it could not use any of them and went into low graphics mode.

Any suggestions? Thanks.

---

### Post by Fixman on 2008-04-05
Press ctrl->alt->+ and ctrl->alt->- (from the numpad) until resolution is correct.

---

### Post by paul905 on 2008-04-05
Unfortunately that just cycles me through the 3 lower res options available on the Screens & Graphics panel :-(

---

### Post by paul905 on 2008-04-05
FWIW the graphics are AMD 690G chipset.

I'm thinking of taking the monitor back if I can't resolve this.

---

### Post by energy. on 2008-04-05
I don't know how to fix this but I did a google search and found a site saying that the maximum supported 2D resolution of that chipset is 2048x1536 so I believe that a solution is out there.

---

