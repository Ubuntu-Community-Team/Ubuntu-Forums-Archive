---
title: "Xinerama second monitor only starts after restarting the X server"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by ttolstead on 2006-12-10
I have recently converted from Suse 10.1 to Edgy.  I find Edgy to be superior in most ways.  The one issue I have encountered is that Xinerama will not start on boot.  That is, when  I boot the system, my primary LCD comes up just fine, but my secondary LCD does not start until I restart the x server (ctrl alt bksp).  I have tried many different suggestions, to no avail.

Any suggestions as to how to address this issue would be apreciated.  I have included the following detail.

This is what I think is the pertinent portion of my xorg.conf:

ection "ServerFlags" 
        Option "Xinerama" "on" 
EndSection

Section "Device"

	Identifier	"Matrox Graphics, Inc. MGA G550 AGP 0"
	Driver		"mga"
	BusID		"PCI:1:0:0"
	Screen 0
	Option "backingstore"
	Option "AGPMode" "4"

EndSection

Section "Device"

	Identifier	"Matrox Graphics, Inc. MGA G550 AGP 1"
	Driver		"mga"
	BusID		"PCI:1:0:0"
	Screen 1
	Option "backingstore"
	Option "AGPMode" "4"

EndSection

Section "Monitor"
	Identifier	"LW98 0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"LW98 1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen 0"
	Device		"Matrox Graphics, Inc. MGA G550 AGP 0"
	Monitor		"LW98 0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Default Screen 1"
	Device		"Matrox Graphics, Inc. MGA G550 AGP 1"
	Monitor		"LW98 1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen 0"
	Screen		"Default Screen 1" RightOf "Default Screen 0"
	Option "Xihnerama" "on"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

# Section "DRI"
#	Mode	0666
# EndSection

Section "ServerFlags"
	Option "Xinerama"
EndSection

When xinerama is up and running the errors in xorg.log are:

(EE) MGA(0): [drm] DRIScreenInit failed.  Disabling DRI.
(EE) MGA(1): Not initializing the DRI on the second head
(EE) AIGLX: Screen 1 is not DRI capable

Which appear to be because 3D acceleration is not supported by xinerama.

When xinerama fails on boot the errors in xorg.log are:

(EE) MGA(0): [drm] DRIScreenInit failed.  Disabling DRI.

(EE) MGA(1): Not initializing the DRI on the second head

(EE) AIGLX: Screen 1 is not DRI capable

Perhaps this issue is related to diabling 3d accelleration?

---

### Post by ttolstead on 2006-12-10
I just noted the typo in the 
"Option "Xihnerama" "on"" statement in the section "ServerLayout", and corrected it and tested it.  It did not make any difference, perhaps this option is inappropriate in this context?

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen 0"
Screen "Default Screen 1" RightOf "Default Screen 0"
Option "Xihnerama" "on"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

---

### Post by peterm34 on 2007-08-17
Hi, Having (finally) got G550 card running successfully in dual display, I have exactly the same problem as you: on startup the output of the second display channel is disabled (the monitor displays "No video input").  The system is in wide desktop mode (evidenced by the shape of the workspace idons at the bottom of the screen, and the ability to drag windows off to where the second display should be!)  I can turn the output on by switching to a text console (Ctrl-Alt-F1) - I get 2 identical displays - and back again (Ctrl-Alt-F7) - I get the full X dual-monitor display.  I can do this either before or after logging in.  I expect Ctrl-Alt-Bksp would work in the same way, but I haven't tried it yet.

My xorg.conf is substantially similar to yours, so I'm not attaching it unless somebody would like to see it.

Have you solved this problem yet?  If not, does anybody have any ideas?  Is there an additional command we could put in xorg.conf to turn on the output?   All thoughts would be much appreciated. :)

Peter

---

### Post by bryceharrington on 2007-09-28
The 1440x1440 resolutions are clearly incorrect (see [https://bugs.launchpad.net/ubuntu/+source/xresprobe/+bug/115220](https://bugs.launchpad.net/ubuntu/+source/xresprobe/+bug/115220)).  I don't know if they're causing the Xinerama problems but they shouldn't be there.  Either delete them all or correct them (perhaps 1440x900 or 1440x1280 or whatever would be better.)

---

