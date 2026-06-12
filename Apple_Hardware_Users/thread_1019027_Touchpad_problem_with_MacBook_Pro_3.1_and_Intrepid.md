---
title: "Touchpad problem with MacBook Pro 3.1 and Intrepid"
date: 2008-12-22
forum: Apple Hardware Users
---

### Post by [woodstock] on 2008-12-22
Hello,

I just updated from Hardy to Intrepid via dist-upgrade. All went well so far, however I experienced some problems with the touchpad.
The Kernel module is loaded (appletouch) but the xserver is ignoring my configuration.  I had a very sophisticated InputDevice section for the xorg.conf, but all settings there are ignored in Intrepid, unfortunately. I already read the hints in the [wiki page]("https://help.ubuntu.com/community/MacBookPro3-1/Intrepid"), but the touchpad persistently ignores all settings. It even behaves completely different. There is no scrolling at all, right click is achieved by tapping with three fingers instead of two etc. I put ```
<merge key="input.x11_options.ClickFinger2" type="string">3</merge>
```, of course.)

It doesn't matter if I rename the .fdi-file to 
**/etc/hal/fdi/policy/appletouch.fdi**
or 
**/etc/hal/fdi/policy/bcm5974.fdi**
as stated in the wiki page. The touchpad still ignores all settings. (I'm not sure, if the statement in the wiki page applies to the MBP 3.1, actually. For the MPB there is no bcm5974 device, and the kernel module loaded is the appletouch module.)

I I read the configuration file correctly, I should be possible to start synclient, however doing
```
synclient -l
```
results in an error
```
Can't access shared memory area. SHMConfig disabled?
```

I deduce, that there is something terrible wrong with my configuration.

Any help?

---

### Post by cyberdork33 on 2008-12-24
You should have appletouch. The fdi file name doesn't matter the are parsed either way.

SHMconfig doesn't work unless enabled in the xorg.conf manner.

Settings in xorg.conf and your fdi file conflict and cause issues. make sure you use only one or the other.

---

### Post by [woodstock] on 2008-12-24
Hi cyberdork33!

Using only the xorg.conf does the trick. I don't know why the touchpad won't work using hal, but frankly I can't make myself care anymore. There is [another problem]("http://ubuntuforums.org/showthread.php?t=1019637") concerning the "beauty of configuration", and all my hopes of having consistent configuration with no tweaks are gone anyway.

For all who encounter the same/a similar problem:

Remove the XML configuration file (appletouch.fdi or bcm5974.fdi) in */etc/hal/fdi/policy/*.
Then, configure your touchpad the old-fashioned way in **/etc/X11/xorg.conf**, for example like this:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"CorePointer"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"

	Option          "LeftEdge"              "20"
	Option          "RightEdge"             "1050"
	Option          "TopEdge"               "10"
        Option          "BottomEdge"            "360"
        Option          "FingerLow"             "10"
        Option          "FingerHigh"            "30"
        Option          "MaxTapTime"            "180"
        Option          "MaxTapMove"            "220"
	Option          "MaxDoubleTapTime"      "180"
	Option          "SingleTapTimeout"      "180"
	Option          "ClickTime"             "100"
	Option          "FastTaps"              "1"
	Option          "EmulateMidButtonTime"  "75"
	Option          "VertScrollDelta"       "15"
	Option          "HorizScrollDelta"      "50"
        Option          "VertEdgeScroll"        "1"
        Option          "HorizEdgeScroll"       "1"
        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1"
        Option          "MinSpeed"              "0.9"
        Option          "MaxSpeed"              "1.0"
        Option          "AccelFactor"           "0.0025"
        Option          "EdgeMotionMinZ"        "40"
        Option          "EdgeMotionMaxZ"        "86"
        Option          "EdgeMotionMinSpeed"    "1"
        Option          "EdgeMotionMaxSpeed"    "400"
        Option          "EdgeMotionUseAlways"   "0" 	 
        Option          "UpDownScrolling"       "1"
        Option          "LeftRightScrolling"    "1"
        Option          "UpDownRepeat"          "1"
        Option          "LeftRightRepeat"       "1"
        Option          "ScrollButtonRepeat"    "100"
        Option          "TouchpadOff"           "0"
        Option          "GuestMouseOff"         "0"
        Option          "LockedDrags"           "0"
        Option          "RTCornerButton"        "4"
        Option          "RBCornerButton"        "5"
        Option          "LTCornerButton"        "2"
        Option          "LBCornerButton"        "2"
        Option          "TapButton1"            "1"
        Option          "TapButton2"            "3"
        Option          "TapButton3"            "2"
        Option          "CircularScrolling"     "1"
        Option          "CircScrollDelta"       "0.1"
        Option          "CircScrollTrigger"     "3"
        Option          "CircularPad"           "1"
        Option          "PalmDetect"            "1"
        Option          "PalmMinWidth"          "15"
        Option          "PalmMinZ"              "40"
        Option          "CoastingSpeed"         "0"
        Option          "PressureMotionMinZ"    "40"
        Option          "PressureMotionMaxZ"    "160"
        Option          "PressureMotionMinFactor" "1"
        Option          "PressureMotionMaxFactor" "1"
 EndSection
```

Make sure, that the device is enabled, i.e. remove the comment sign (#) in a later section of the xorg.conf.

```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		0 "Screen0" 0 0
# commented out by update-manager, HAL is now used
#	InputDevice	"Generic Keyboard"
# commented out by update-manager, HAL is now used
#	InputDevice	"Configured Mouse"
# commented out by update-manager, HAL is now used
	InputDevice	"Synaptics Touchpad"
^^^ here
EndSection
```


This works on a MPB 3.1, Intrepid.

Still, if anyone knows how to make the touchpad work using hal and the fdi XML file, please let me know.

---

### Post by hanzomon4 on 2008-12-25
I'm having the same issue

---

