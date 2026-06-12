---
title: "Powerbook trackpad driving me nuts"
date: 2006-06-04
forum: Apple PPC Users
---

### Post by SpazTheCat on 2006-06-04
Hi,

I have a Powerbook G4 1.5Ghz (Powerbookd 5,6) with a synaptics trackpad and it is driving me nuts. When the machine first boots, the trackpad behaves pretty much normally. It is really  sensitive but I probably don't have it tweaked just right yet.

 But, it seems after the machine is on for a while it becomes very erratic and seems to not recognize my finger is on certain parts of the trackpad.

Does anyone else have this issue? Solutions?

Thanks,

Andy

---

### Post by procras on 2006-06-05
If my trackpad misbehaves, I place my palm on it to reset it!

If it is really annoying me. I plug in a usb mouse and
$ sudo rmmod appletouch

:D

---

### Post by dombleu on 2006-06-05
On my side too, i just plug a USB mouse most of the time. But it is sure nice to have a fully working laptop nevertheless. And because my touchpad was acting weird too, I ended up playing with /etc/X11/xorg.conf and found that config somewhere in these forums. And it works wonderfully eversince. Give it a try! Just backup your xorg.conf, and change the section regarding the touchpad for that one:

```
Section "InputDevice"
    Identifier    	"Synaptics Touchpad"
    Driver        	"synaptics"
    Option		"AlwaysCore"
    Option        	"SendCoreEvents"    "true"
    Option        	"Device"        "/dev/input/event2"
    Option        	"Protocol"        "event"
    Option 		"LeftEdge" "130"
    Option 		"RightEdge" "840"
    Option		"TopEdge" "130"
    Option 		"BottomEdge" "640"
    Option 		"FingerLow" "7"
    Option		"FingerHigh" "8"
    Option		"MaxTapTime" "180"
    Option		"MaxTapMove" "110"
    Option		"ClickTime" "0"
    Option		"EmulateMidButtonTime" "75"
    Option		"VertScrollDelta" "20"
    Option		"HorizScrollDelta" "20"
    Option		"MinSpeed" "0.60"
    Option		"MaxSpeed" "1.10"
    Option		"AccelFactor" "0.030"
    Option		"EdgeMotionMinSpeed" "200"
    Option		"EdgeMotionMaxSpeed" "200"
    Option		"UpDownScrolling" "1"
    Option		"CircularScrolling" "1"
    Option		"CircScrollDelta" "0.1"
    Option		"CircScrollTrigger" "2"
    Option		"SHMConfig" "on"
    Option		"Emulate3Buttons" "on"
EndSection

```

and restart your X server. (Log out and in again.)

Good luck!

---

