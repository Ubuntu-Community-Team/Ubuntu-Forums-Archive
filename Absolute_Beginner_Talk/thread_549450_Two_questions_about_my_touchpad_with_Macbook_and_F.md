---
title: "Two questions about my touchpad with Macbook and Feisty"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by dmber on 2007-09-12
My touchpad is way too fast.  

This is my Synaptics Touchpad portion of my xorg.conf.  I'm on a Macbook running Feisty.  I've turned Acceleration and Sensitivity all the way down in Preferences.  Then I tried turning sensitivity way up, which makes it a little better.  I just can't get it to slow down enough.

```
Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "LeftEdge" "150"
	Option "RightEdge" "1070"
	Option "TopEdge" "100"
	Option "BottomEdge" "310"
	Option "FingerLow" "25"
	Option "FingerHigh" "30"
	Option "MaxTapTime" "180"
	Option "MaxTapMove" "220"
	Option "MaxDoubleTapTime" "180"
	Option "HorizEdgeScroll" "0"
	Option "VertEdgeScroll" "0"
	Option "TapButton1" "0"
	Option "TapButton2" "0"
	Option "TapButton3" "0"
	Option "LockedDrags" "off"
	Option "VertScrollDelta" "20"
	Option "HorizScrollDelta" "50"
	Option "VertTwoFingerScroll" "1"
	Option "HorizTwoFingerScroll" "1"
	Option "MinSpeed" "1.10"
	Option "MaxSpeed" "1.30"
	Option "AccelFactor" "0.08"
	Option "Emulate3Buttons" "true"
	Option "SHMConfig" "on"		# corner buttons
	Option "RTCornerButton" "0"
	Option "RBCornerButton" "3"
	Option "LTCornerButton" "0"
	Option "LBCornerButton" "2"
EndSection
```

My second question is that I have it set up to where the bottom left corner of my touchpad is middle-click and the bottom right corner is right-click, but I'd like to just use the button to click -- no tapping.  I'd like click to be left-click, 1 finger on the touchpad + click = middle-click, and two-finger + click = right click (like OS X).

Is that possible?

Thanks!

---

### Post by startherepodcast on 2007-09-13
[http://ubuntuforums.org/showthread.php?t=493758](http://ubuntuforums.org/showthread.php?t=493758)

There you are, this seems like a good HOWTO, although I don´t run a MacBook, I whish I did though..

Also there is a special Ubuntu MacBook Community:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Hope I could help you, have fun!

---

### Post by dmber on 2007-09-14
thanks for  the links, but that's how i got my trackpad working in its current form.

---

