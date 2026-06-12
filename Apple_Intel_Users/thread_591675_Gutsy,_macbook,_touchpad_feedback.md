---
title: "Gutsy, macbook, touchpad: feedback"
date: 2007-10-25
forum: Apple Intel Users
---

### Post by NicS on 2007-10-25
Hi all,

I just installed gutsy on my macbook 1st gen, 1.83ghz macbook
Thanks for the people who wrote:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
great help.
It works flawlessly suspend, hibernate, wifi, without recmpliing anything or modifying the kernel.
Mighty mouse works, after a hidd -connect though

Anyway, this post is to give you my touchpad configuration, the only really badly configured thing out of the box. This has to be compared to the ubuntu wiki page.

I like it to be the same as on the original macbook, so in xorg.conf.

Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
....
        Option "TapButton1" "0" // disable one tap, left click
        Option "TapButton2" "3" // two finger tap, right click
        Option "TapButton3" "2" // three finger, middle click
...
        Option "SHMConfig" "on" // to use syndeamon
EndSection

If you don't prevent the touchpad from working while tapping, the macbook is barely usable (I use it for work, and extensive use of the terminal). 
Here's a config I like mixing what I found on the web (put this in your session startup):

syndaemon -d -K -i 0.5

-d : prevent touchpad events while tapping
- i 0.5: default is 2 seconds which is really too long for me.
- K: is when you figure out that ctrl-click does not work on webpages anymore, so you can still make your combos working while disabling the touchpad.

Hope this helps others, and that we can end up with a really sweet touchpad config at the end of this thread

---

### Post by LeopoldBloom on 2007-11-07
I have a MacBook Pro I might try this to and see if it works for that. Thanks!

---

### Post by ChardFi on 2007-11-08
Did it work on your mac book pro mate?

---

### Post by dmber on 2007-11-08
i'm a fan of the bottom corners for middle and right click.

i tap the bottom left corner for middle click and the bottom right corner for right click.  i hit the ..."clicker" for single click.

---

### Post by ronocdh on 2007-11-09
> **dmber said:**
> i'm a fan of the bottom corners for middle and right click.

i tap the bottom left corner for middle click and the bottom right corner for right click.  i hit the ..."clicker" for single click.
I prefer two finger tap for right click, three finger tap for middle click. I go back and forth between setting one finger tap as left click. 

I'd really like to get two-finger scrolling working well!

---

### Post by dmber on 2007-11-09
this is my Synaptics Touchpad section from my xorg.  it's got button clicking as i described earlier and two finger scrolling:

Section "InputDevice"
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
	Option "SHMConfig" "on"
	# corner buttons
	Option "RTCornerButton" "5"
	Option "RBCornerButton" "3"
	Option "LTCornerButton" "4"
	Option "LBCornerButton" "2"
EndSection

---

