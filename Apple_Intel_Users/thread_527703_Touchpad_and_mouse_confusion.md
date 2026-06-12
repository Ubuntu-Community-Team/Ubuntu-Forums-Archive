---
title: "Touchpad and mouse confusion"
date: 2007-08-16
forum: Apple Intel Users
---

### Post by Adorack on 2007-08-16
I have the touchpad on my 1st-generation Mac Book Pro configured properly (scrolling works, two-finger-tap works) with the exception of one thing: whatever is set to disable the touchpad while I'm typing instead disables my mouse.  

This is really annoying--not only is it impossible to type on the laptop keyboard because the touchpad randomly gets triggered; but whenever I'm typing and then try to use the mouse, there's a delay.  I've tried searching the forums and the internet, but all I can find is information on how to enable the delay.

Please tell me if you know what's wrong.

Xorg.conf:
```


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option 		"SHMConfig" "on"
	Option		"CorePointer"
	Option		"SendCoreEvents" "true"
	Option		"Device" "/dev/psaux"
	Option 		"Protocol" "auto-dev"
	Option 		"LeftEdge" "100"
	Option 		"RightEdge" "1120"
	Option 		"TopEdge" "50"
	Option 		"BottomEdge" "310"
	Option 		"FingerLow" "20"
	Option 		"FingerHigh" "30"
	Option 		"MaxTapTime" "150"
	Option 		"MaxTapMove" "220"
	Option 		"MaxDoubleTapTime" "180"
	Option 		"VertScrollDelta" "25"
	Option 		"VertTwoFingerScroll" "true"
	Option 		"TapButton2" "3"
	Option 		"TapButton3" "2"
	Option 		"MinSpeed" "0.79"
	Option 		"MaxSpeed" "0.88"
	Option 		"AccelFactor" "0.015"
EndSection

Section "InputDevice"
       Identifier "Configured Mouse"
       Driver "mouse"
       Option "CorePointer"
       Option "Device" "/dev/input/mice"
       Option "Protocol" "ExplorerPS/2"
       Option "ZAxisMapping" "4 5"
       Option "Emulate3Buttons" "true"
       Option "Buttons" "7"
       Option "ButtonMapping" "1 2 3 6 7"
EndSection


```

---

