---
title: "Laptop Mouse Speed"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by adds2one on 2006-08-01
Hi,

I have just installed Ubuntu on my laptop. I am finding that the speed of the mouse pad is too slow for my liking but when I adjust the mouse settings under System->Preferences->Mouse->Motion I get no change. 

It seems to me that my mouse is not what is being referenced in Gnome. Can anyone help me to fix this?

Here is the relevant section of my /etc/X11/xorg.conf file:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection
```

Thanks - J

---

### Post by kenjo on 2006-08-06
I have the same problem here... need more speed on the touchpad, but the settings don't have any affect.

---

### Post by 5-HT on 2006-08-06
The mouse settings will not affect your touchpad, if that's what you're trying to configure.
To configure the touchpad see:[ http://www.ubuntuforums.org/showthread.php?t=229302]("http://www.ubuntuforums.org/showthread.php?t=229302")

---

### Post by dsgilbert on 2006-08-06
I used the following post to configure my laptop mouse (ALPS GlidePoint) device. After making the configuration changes you should download and install qsynaptics to configure your touchpad.

[http://www.ubuntuforums.org/showthread.php?t=78904&highlight=qsynaptics](http://www.ubuntuforums.org/showthread.php?t=78904&highlight=qsynaptics)

My configuration looks like this...

Find the handler (in this case "event3") for the touchpad...

david@david-laptop:~$  **cat /proc/bus/input/devices**

: Bus=0011 Vendor=0002 Product=0008 Version=6337
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse1 **event3** ts1
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003


Modificiations made to /etc/X11/xorg.conf

(try cutting and pasting the section below using the command (sudo gedit /etc/X11/xorg.conf)

Section "InputDevice"
	Identifier "ALPS"
	Driver "synaptics"
	Option "AlwaysCore"
	Option "Device" "/dev/input/**event3**"
	Option "Protocol" "event"
	Option "LeftEdge" "120"
	Option "RightEdge" "830"
	Option "TopEdge" "120"
	Option "BottomEdge" "650"
	Option "FingerLow" "14"
	Option "FingerHigh" "15"
	Option "MaxTapTime" "180"
	Option "MaxTapMove" "110"
	Option "ClickTime" "0"
	Option "EmulateMidButtonTime" "75"
	Option "VertScrollDelta" "10"
	Option "HorizScrollDelta" "0"
	Option "MinSpeed" "0.45"
	Option "MaxSpeed" "0.75"
	Option "AccelFactor" "0.020"
	Option "EdgeMotionMinSpeed" "200"
	Option "EdgeMotionMaxSpeed" "200"
	Option "UpDownScrolling" "1"
	Option "CircularScrolling" "0"
	Option "CircScrollDelta" "0.1"
	Option "CircScrollTrigger" "2"
	Option "SHMConfig" "true"
EndSection


section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"**ALPS**"
EndSection

---

### Post by kenjo on 2006-08-06
Thanks.  I just went into my xorg.conf and put in the lines

Option "MinSpeed" "0.45"
Option "MaxSpeed" "0.75"
Option "AccelFactor" "0.020"

from that post, then adjusted them to my liking and everything is working great.  I'll probably play with the other options later, but right now that's perfect.

---

### Post by cedance on 2007-10-04
yes, these 3 commands inserted into the xorg.conf works great!!

thk you very much!!

cedance.

---

### Post by raucous1 on 2008-01-03
Me three. The gnome applet doesn't work at all, but this fixed it.

---

