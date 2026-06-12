---
title: "Please Submit Your Xorg.conf To Support iBook/Powerbook Users!"
date: 2006-07-29
forum: Apple PPC Users
---

### Post by zachws on 2006-07-29
*If you have a **synaptic touchpad** please read on*

Please submit the section of your xorg.conf that applies to **synaptics touchpad**. For example:

```
[B]Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"[/B]
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "LeftEdge"              "120"
        Option          "RightEdge"             "830"
        Option          "TopEdge"               "120"
        Option          "BottomEdge"            "650"
        Option          "FingerLow"             "14"
        Option          "FingerHigh"            "15"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "110"
        Option          "EmulateMidButtonTime"  "75"
        Option          "VertScrollDelta"       "20"
        Option          "HorizScrollDelta"      "20"
        Option          "MinSpeed"              "0.3"
        Option          "MaxSpeed"              "0.75"
        Option          "AccelFactor"           "0.015"
        Option          "EdgeMotionMinSpeed"    "200"
        Option          "EdgeMotionMaxSpeed"    "200"
        Option          "UpDownScrolling"       "1"
        Option          "CircularScrolling"     "1"
        Option          "CircScrollDelta"       "0.1"
        Option          "CircScrollTrigger"     "2"
EndSection
```

This is so those of us with slow/disfunctional trackpads can use and enjoy Ubuntu and it's derivatives.

Thanks a lot,
Zach

---

### Post by rasec on 2006-07-29
Zach, does you ibook even support the synaptics driver? I have an older powerbook which uses the adb bus and for some reason the ubuntu installer configured my mouse to use the synaptics driver under xorg. I did find a kernel patch for the 2.6.17 kernel [here]("http://www.artha.org/shammash/ppc/adb_syn/") if your interested. You only need this patch if you have an older mac that uses the adb bus.

To check to see if you mouse uses the adb bus:

```
grep -i adb /proc/bus/input/devices
```

If you see anything that references adb mouse, than the synaptics driver isn't going to do anything.

By the way, if I'm not mistaken, the only advantage to the synaptics driver of over the adb driver is the ability to enable scrolling. If you want to emulate more mouse buttons you can always try mouseemu.

---

### Post by zachws on 2006-07-29
Thanks for the reply. I am on a quest to get my mouse working. I will try this. I have the latest iBook G4 ever made [a little disappointing :)].

---

### Post by rasec on 2006-07-29
What's wrong with your mouse? Anyway, if you want to configure the synaptics driver, either look at the synaptics man page or install ksynaptics or qsynaptics. If you go with the latter, you may need need to add SHMConfig in the synaptics section in your xorg.conf. 

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SHMConfig"     "on"
....
EndSection

```

You should be aware that the readme file for the xorg synaptics driver states:

>    SECURITY NOTE! This is not secure if you are in an untrusted
   multiuser environment. All local users can change the parameters at any
   time.


Since your laptop isn't exactly a multiuser environment, you should be able to use this option without any problems.

If you don't want to install [kq]synaptics and you enabled SHMConfig, you can always use synclient to tweak the synaptics driver on the fly. The changes won't permanent though, so once you get the driver working the way you like it you'll have to add those changes to the xorg.conf. See the synclient man page for more details.

---

### Post by Uta on 2006-07-30
For what it's worth here is mine. I have both an USB 2 button(and scroll wheel) mouse working and the touchpad.
-------------------------------
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

---

### Post by APU on 2006-07-30
I think I found the solution (for me at least)

I have one of the last generation 12" PowerBooks (1.5 Ghz G4) and the USB scrolling trackpad. I also experienced the problems with a veeeeeery slow trackpad response and tried out quite a lot of different xorg.conf settings wich i found online as well as configuring it by using qsynaptic.

Looking at the qsynaptic config file i decided to try out the settings one by one and found a quite easy solution. I set the MinSpeed and MaxSpeed Options which should is quite straightforward. Then i set the AccelFactor to a value as high as I didn´t find anywhere on the Net - and it worked.

Currently my xorg.conf Trackpad Section looks like this:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option          "AccelFactor"           "0.07"
        Option          "MinSpeed"              "0.6"
        Option          "MaxSpeed"              "1.3"
        Option          "SHMConfig"             "on"
EndSection

There is no fancy stuff like clicking and scrolling in it but the cursor movement works quite well already. I think this is a good starting point for including more and more options since it is enough to be able to really use the trackpad.

I think the last Option "SHMConfig" is not necessary - I just needed it for qsynaptics to work and did not yet delete it.

APU

---

