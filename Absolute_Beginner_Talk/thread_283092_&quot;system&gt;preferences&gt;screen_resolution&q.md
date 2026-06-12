---
title: "&quot;system&gt;preferences&gt;screen resolution&quot; disabled"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Graybeard on 2006-10-23
On first installing Ubuntu 6.06 I immediately changed the screen resolution down to 1024 x 768 to make the display readable to these old eyes.

Now I have successfully changed the display to portrait format by adding "Option "Rotate" "ccw"" to the xorg.conf file. Unfortunately, resolution reverted to 1280 x 1024 and going to System>preferences>screen-resolution yields the error message "The X server does not support the XRandR extension. Runtime resolutions changes to the display size are not available."

How can I have both portrait format and 1024 x 768 resolution?

The relevant portion of xorg.conf follows:

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 420]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	**Option		"Rotate" "ccw"**
EndSection

Section "Monitor"
	Identifier	"VP920 Series"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 420]"
	Monitor		"VP920 Series"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

### Post by tzulberti on 2006-10-23
You should trie editin xorg using the following commando:
sudo dpkg-reconfigure xserver-xorg

---

### Post by Graybeard on 2006-10-24
> **tzulberti said:**
> You should trie editin xorg using the following commando:
sudo dpkg-reconfigure xserver-xorg

OK, I followed tzulberti's advice but then was left with "normal" orientation. But further searching brought XRandR to my attention, so I tried to change to portrait format as follows, and got the errors listed. Where do I go from here? Specifically, where do I find explanations of the error messages?

```
bob@bob-dell:/etc/X11$ sudo xrandr -o left
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  152 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12
bob@bob-dell:/etc/X11$ 
```

---

