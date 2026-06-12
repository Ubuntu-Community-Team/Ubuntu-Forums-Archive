---
title: "Unable to modify synaptics options on macbook."
date: 2008-07-20
forum: Apple Hardware Users
---

### Post by excrabot on 2008-07-20
I have managed to get my trackpad to load on startup after some help in another thread here..

[http://ubuntuforums.org/showthread.php?t=849837&highlight=trackpad](http://ubuntuforums.org/showthread.php?t=849837&highlight=trackpad)

Now i'm having trouble modifying the xorg.conf file to adjust the various option that i prefer,. side scrolling, top corner button taps for right click etc.

after modifying the xorg, i restart X but nothing changes. i only have basic tackpad functionlity, no scrolling or tapping.

i've run through the sticky on the synaptics thread and followed all of those points to no avail.


here's my xorg.conf :

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"CorePointer"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"SHMConfig"		"true"
	Option 		"LeftEdge" 		"100"
	Option		"RightEdge" 		"1100"
	Option 		"TopEdge" 		"50"
	Option 		"BottomEdge" 		"300"
	Option 		"MaxTapTime" 		"180"
	Option 		"MaxTapMove" 		"220"
	Option 		"MaxDoubleTapTime" 	"180"
	Option		"VertEdgeScroll"	"true"
	Option 		"VertScrollDelta" 	"25"
	Option 		"HorizScrollDelta" 	"30"
	Option 		"VertTwoFingerScroll" 	"true"
	Option 		"HorizTwoFingerScroll" 	"true"
	Option 		"FastTaps" 		"true"
	Option 		"TapButton2" 		"3"
	Option 		"TapButton3" 		"2"
	Option 		"MinSpeed" 		"1.10"
	Option 		"MaxSpeed" 		"2.10"
	Option 		"AccelFactor" 		"0.35"
	Option 		"Emulate3Buttons" 	"true"
	Option 		"RTCornerButton" 	"0"
	Option 		"RBCornerButton" 	"3"
	Option 		"LTCornerButton" 	"0"
	Option 		"LBCornerButton" 	"2"
	Option		"GrabEventDevice"	"0"
EndSection

i've been trying to get it sorted out for days, and have posted this out of frustration.

---

