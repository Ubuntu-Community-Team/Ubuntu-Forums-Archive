---
title: "&quot;clicking&quot; problem with touchpad"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by machavillain on 2007-11-09
I used 7.04 with no problem; now after doing a clean 7.10 install, as I move my mouse around the screen, it seems to click on everything I scroll over. I've turned off "tap to click" in Mouse settings. I am using an HP laptop - stats in my signature.

Any ideas on what the problem is?

---

### Post by machavillain on 2007-11-09
Any ideas? The pointer also seems to be a bit shakey, despite playing around with the settings.

Again, this worked fine in Feisty, so I think it's a software problem.

---

### Post by VitaminBB on 2007-11-11
I get the same problem ...

I will be dragging my mouse on the screen and it clicks onto something when I didnt press click at all ...

This is a problem I had with feisty and I was hoping it would be solved in Gutsy, apparently not ...

---

### Post by jordanmthomas on 2007-11-11
relevant options from mouse part of xorg.conf:
```
Section "InputDevice"
    Identifier		"Mouse3"
    Driver		"synaptics"

        Option      "Device"                "/dev/psaux"
    Option      "Protocol"              "auto-dev"
    Option      "LeftEdge"              "120"
    Option      "RightEdge"             "830"
    Option      "TopEdge"               "120"
    Option      "BottomEdge"            "560"  # comment out this entire line to disable horizontal scroll/click ability
    Option      "FingerLow"             "14"
    Option      "FingerHigh"            "15"
    Option      "EmulateMidButtonTime"  "70"
    Option      "VertScrollDelta"       "20"
    Option      "HorizScrollDelta"      "0"
   [COLOR="Red"] Option      "MaxTapTime"            "0"    # 0 disables tap-to-click, set it to 100 to re-enable[/COLOR]
    Option      "MinSpeed"              "0.3"
    Option      "MaxSpeed"              "0.75"
    Option      "AccelFactor"           "0.015"
    Option      "EdgeMotionMinSpeed"    "200"
    Option      "EdgeMotionMaxSpeed"    "200"
    Option      "UpDownScrolling"       "1"
    Option      "LeftRightScrolling"    "0"
    Option      "CircularScrolling"     "0"

#Option		"SendCoreEvents"	"true"
#    Option		"Device"		"/dev/psaux"
#    Option		"Protocol"		"auto-dev"
#    Option		"HorizScrollDelta"	"0"
    Option		"SHMConfig"		"on"
    # For ALPS TouchPads
#    Option		"MaxSpeed"		"0.7"
#    Option		"MinSpeed"		"0.18"
#    Option		"AccelFactor"		"0.08"
#    Option		"TopEdge"		"120"
#    Option		"LeftEdge"		"120"
#    Option		"BottomEdge"		"830"
#    Option		"RightEdge"		"650"
#   Option		"FingerLow"		"25"
#    Option		"FingerHigh"		"30"
    # Do you keep moving the mouse while typing? Try this trick.
    #synclient TouchpadOff=1 disable your synaptics touchpad
    #synclient TouchpadOff=0 enable your synaptics touchpad
EndSection
```

Most of this won't be in there, but you can add it.

---

### Post by VitaminBB on 2007-11-11
Thats awesome ...

Your proposing I disable the touch to click option, should I assume that 100 is the default and a higher number makes it harder to "touch to click" and therefore would avoid the misfires?

---

### Post by jordanmthomas on 2007-11-11
I just disable the tapping on my computer because it's so annoying.  I can be typing and it just clicks for no reason.  

But yes, higher values should make it harder to click with it.  ( I am not sure on this though...100 may mean 100% or something...I've never really played with it)

---

### Post by VitaminBB on 2007-11-11
> # bare-bones XFree86 config to start the server in probe-only mode
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	RgbPath		"/etc/X11/rgb.txt"
EndSection
Section "ServerFlags"
	Option "AllowMouseOpenFail"
EndSection
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"int10"
	Load	"record"
	Load	"vbe"
EndSection
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection
Section "InputDevice"
	Identifier	"Generic Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
EndSection
Section "Device"
	Identifier	"Generic Device"
	Driver		"::DRIVER::"
EndSection
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Generic Mouse"
EndSection

This is what my xorg.conf file says ...

Where and what exactly should I add the information I need to ?

---

### Post by jordanmthomas on 2007-11-11
It looks like you don't have a section for the touchpad.
What you can do is this:
1.  Add a new section (you can copy and paste my whole section I posted earlier to the end of the file)
2.  In the "ServerLayout" section (currently at the very end of your file) add this line:
```
InputDevice     "Mouse3"
```

Remember to back up your xorg.conf in the event it doesn't like your changes.
Also, I am not sure how well this will work since you appear to be using the new xserver that sets itself up on the fly.  I'm using this as well, but I still use a full xorg.conf that I've used for years now.

---

### Post by anewguy on 2007-11-12
Have you tried installing gsynaptics from the synaptic package manager?  That's all I've ever needed to do with a laptop, plus adding the option

Option "SHMConfig" "true"

to the touchpad section of xorg.conf

This gives you an actual utility accessable under System/Preferences to set several thing on your touchpad, including turning off or on the touch tapping.  This is the preferred way in comparison to making the bigger changes to xorg.conf.

If you're not sure about this, just search this forum for the keyword gsynaptics and you should find all you need to know.:)

---

### Post by VitaminBB on 2007-11-12
Thanks both of you guys, your advice worked :)

---

### Post by buccaneere on 2007-11-25
> **jordanmthomas said:**
> relevant options from mouse part of xorg.conf:
```
Section "InputDevice"
    Identifier		"Mouse3"
    Driver		"synaptics"

        Option      "Device"                "/dev/psaux"
    Option      "Protocol"              "auto-dev"
    Option      "LeftEdge"              "120"
    Option      "RightEdge"             "830"
    Option      "TopEdge"               "120"
    Option      "BottomEdge"            "560"  # comment out this entire line to disable horizontal scroll/click ability
    Option      "FingerLow"             "14"
    Option      "FingerHigh"            "15"
    Option      "EmulateMidButtonTime"  "70"
    Option      "VertScrollDelta"       "20"
    Option      "HorizScrollDelta"      "0"
   [COLOR="Red"] Option      "MaxTapTime"            "0"    # 0 disables tap-to-click, set it to 100 to re-enable[/COLOR]
    Option      "MinSpeed"              "0.3"
    Option      "MaxSpeed"              "0.75"
    Option      "AccelFactor"           "0.015"
    Option      "EdgeMotionMinSpeed"    "200"
    Option      "EdgeMotionMaxSpeed"    "200"
    Option      "UpDownScrolling"       "1"
    Option      "LeftRightScrolling"    "0"
    Option      "CircularScrolling"     "0"

#Option		"SendCoreEvents"	"true"
#    Option		"Device"		"/dev/psaux"
#    Option		"Protocol"		"auto-dev"
#    Option		"HorizScrollDelta"	"0"
    Option		"SHMConfig"		"on"
    # For ALPS TouchPads
#    Option		"MaxSpeed"		"0.7"
#    Option		"MinSpeed"		"0.18"
#    Option		"AccelFactor"		"0.08"
#    Option		"TopEdge"		"120"
#    Option		"LeftEdge"		"120"
#    Option		"BottomEdge"		"830"
#    Option		"RightEdge"		"650"
#   Option		"FingerLow"		"25"
#    Option		"FingerHigh"		"30"
    # Do you keep moving the mouse while typing? Try this trick.
    #synclient TouchpadOff=1 disable your synaptics touchpad
    #synclient TouchpadOff=0 enable your synaptics touchpad
EndSection
```

Most of this won't be in there, but you can add it.

Yeah - it sure don't be in there. But this be in there...

[I]section input device

identifier..............syn touchpad
driver.................synaptics
option................sendcoreevents.............. true
option................device...................... ....dev/psaux
option................protocol.................... ....auto-dev
option................horizscrollldelta........... .....0

end section[/I]

---

