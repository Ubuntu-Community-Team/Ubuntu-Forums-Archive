---
title: "Mighty Mouse Bluetooth Hardy - horiz scroll"
date: 2008-06-05
forum: Apple Hardware Users
---

### Post by gforster on 2008-06-05
I know there are other threads out there on the mighty mouse, but my question is specific enough I thought it would warrant a separate thread.

I have all buttons working on the mouse except the horizontal scrolling. When I run the configuration with btnx, it detects the horizontal scrolling as two separate buttons (I named them right and left scroll). I can configure those actions as keyboard commands, though there really isn't anything that corresponds to horizontal scrolling as a keyboard command that I know of. If you know what would be the equivalent, please let me know.

Anyway, when I start xev the buttons are not detected at all. All others on the mouse are. When I test the output of horizontal scrolling in my synaptic touchpad, it detects it as buttons 6 and 7. 

So, is there a way to either bind the horizontal scroll buttons as button 6 and 7?

---

### Post by cyberdork33 on 2008-06-05
see option ZAxisMapping in your Xorg.conf

[http://linux.die.net/man/4/mouse-driver](http://linux.die.net/man/4/mouse-driver)

---

### Post by gforster on 2008-06-05
Thank you for the information on that - however,

the mighty mouse does not even show up in xorg.conf in fact, here are the relative sections of xorg.conf:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"1"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
```

I don't know why it isn't connected through xorg.conf  like I said, everything else about it works just fine.  Is this because of the bluetooth? I don't want to disable my touchpad as I take the thing with me in places where the bluetooth mouse/keyboard just isn't practical.

---

### Post by cyberdork33 on 2008-06-05
This is your mouse device:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection
```

---

### Post by gforster on 2008-06-05
That actually was there before I ever got the mighty mouse. If I reset my xorg.conf and disable my bluetooth connection, I would get that same entry. Also, If I try and add the ```
Option	"ZAxisMapping"	"4 5 6 7"
``` nothing happens. I have also tried using other number combos, still nothing. I even (after backing up, of course) changed that section to look like this: ```
Section "InputDevice"
Identifier "Configured Mouse"
Option "CorePointer"
Driver "evdev"
Option "Name" "Mitsumi Electric Apple Optical USB Mouse"
Option "HWHEELRelativeAxisButtons" "7 6"
Option "Buttons" "8"
EndSection
```

as pointed out in other threads. I feel like this is just beyond my grasp. I know there is an answer somewhere.

what I still don't get is why btnx will pick up on the "buttons," but xev doesn't recognize them.

---

### Post by tntc on 2008-07-08
I was going through my Xorg.0.log (/var/log/Xorg.0.log) when I noticed the following: 

(EE) Apple Mouse: No Device Specified
(EE) PreInit returned NULL for "Apple Mouse"

A little hunting led me to use evtest to hunt around through 
/dev/input/eventN where N is the event device number.

evtest /dev/inut/event9
Input driver version is 1.0.0
Input device ID: bus 0x5 vendor 0x5ac product 0x30c version 0x200
Input device name: "Apple Computer, Inc. Mighty Mouse"
Supported events:
  Event type 0 (Sync)
  Event type 1 (Key)
    Event code 272 (LeftBtn)
    Event code 273 (RightBtn)
    Event code 274 (MiddleBtn)
    Event code 275 (SideBtn)
  Event type 2 (Relative)
    Event code 0 (X)
    Event code 1 (Y)
    Event code 6 (HWheel)
    Event code 8 (Wheel)
  Event type 4 (Misc)
    Event code 4 (ScanCode)
  Event type 20 (Repeat)
Testing ... (interrupt to exit)

So I knew I had my device.

My Xorg.conf section is as follows:

Section "InputDevice"
Identifier "Configured Mouse"
Option "SendCoreEvents" "True"
Option "Device" "/dev/input/event9"
#Note, the Device line can also be set as /dev/input/by-path/<some device>, which is preferable
Driver "evdev"
Option "Name" "Mitsumi Electric Apple Optical USB Mouse"
Option "HWHEELRelativeAxisButtons" "7 6"
Option "Buttons" "8"
EndSection

The only problem is that my mouse clicks are no longer a single event.  I get a stream of clicks, which makes hilighting things...impossible. See [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/223278](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/223278)

---

