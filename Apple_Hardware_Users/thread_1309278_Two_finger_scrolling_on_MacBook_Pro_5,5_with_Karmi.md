---
title: "Two finger scrolling on MacBook Pro 5,5 with Karmic"
date: 2009-11-01
forum: Apple Hardware Users
---

### Post by gigabytes on 2009-11-01
Hello everybody. It's the first post on this forum so I say hello ^^

I have a macbookpro 5,5. It used to work _perfectly_ on ubuntu 9.04 thanks to the wiki page. Now I've installed ubuntu 9.10 (from scratch, not upgraded), and I'm unable to use two finger scrolling on my touchpad. I've done what written on the wiki page as I did with jaunty but now it doesn't work. Two finger scrolling doesn't seem to be active, and I get right edge scrolling instead.

Despite the file installed in /etc/hal/fdi/policy/ contains the values "false" for the edgescrolling keys, I still get right edge scrolling working.

I tried to hack the hal config file without luck. The bcm5974-diagnostics says the configuration is ok, so I guess the driver is loaded. Also I think the hal config file is correctly parsed because I see its options with lshal.

So what can be wrong?
Thank you

---

### Post by andre_orwell on 2009-11-01
I don't have a solution, but it is probably to do with the deprecation of hal. (see [http://www.ubuntu.com/testing/karmic/alpha1](http://www.ubuntu.com/testing/karmic/alpha1) for example).  I'd try doing the X11 configuration using an xorg.conf

---

### Post by gigabytes on 2009-11-01
Thanks, I'll try and post here the results.
But now, if hal-based configuration are being ported to device-kit, then there should be an alternative way to do that thing with device-kit instead of hard-coding the xorg.conf, right?

---

### Post by gigabytes on 2009-11-01
Ok I've tried. It still doesn't work. Again I've explicitly specified that I don't want edge scrolling but I get it anyway. And no sign of two finger scrolling.

Here is my xorg.conf:

Section "InputDevice"
    Identifier "Synaptics Touchpad"
    Driver "synaptics"
    Option "SendCoreEvents" "true"
    Option "Device" "/dev/psaux"
    Option "Protocol" "auto-dev"
    Option "ZAxisMapping" "4 5"
    Option "Emulate3Buttons" "on"
    Option "SHMConfig" "on"
    Option "VertEdgeScroll" "off"
    Option "VertTwoFingerScroll" "true"
    Option "HorizTwoFingerScroll" "true"
    Option "LeftEdge" "85"
    Option "RightEdge" "910"
    Option "TopEdge" "85"
    Option "BottomEdge" "715"
    Option "FingerLow" "25"
    Option "FingerHigh" "30"
    Option "MaxTapTime" "180"
    Option "MaxTapMove" "220"

EndSection

Thank you.

---

### Post by slick666 on 2009-11-01
All I can add is that two finger scrolling worked for me in 9.04 but I upgraded to 9.10 and it doesn't. I'm looking for a solution too.

---

### Post by slick666 on 2009-11-01
Aww it was Sooooooo easy

Go to System -> Preference -> Mouse

Then click on the tab **Touchpad**

Under **Scrolling** select the radio button marked **Two Finger Scrolling**

I also recommend checking the box marked **Enable horizontal scrolling**

---

### Post by volanin on 2009-11-01
This new version of the Xorg Synaptics driver must be configured with xinput.
The fdi file is completely ignored.
This is my configuration:

```
xinput set-int-prop   appletouch "Synaptics Finger"       32 15 25 300
xinput set-int-prop   appletouch "Synaptics Tap Action"   8 0 0 0 0 0 0 0
xinput set-int-prop   appletouch "Synaptics Click Action" 8 1 2 3
xinput set-float-prop appletouch "Synaptics Move Speed"   0.5 2.5 0.1 40
```

The numbers are explained in the manpage.
The new parameters are explained on page 560, section DEVICE PROPERTIES.

```
$ man synaptics
```

The xinput set-int-prop and set-float-prop are explained by the --help option.

```
$ xinput --help
```

To list your current Synaptics configuration, use:

```
$ xinput list-props appletouch
```

Hope that helps.
:)

---

### Post by cyphaw on 2009-11-02
Hi,

I've got problem here too. There are so many places to configure the touchpad :( :
- system -> pref -> mouse, tab touchpad
- system -> pref -> touchpad
- /etc/X11/xorg.conf
- /etc/hal/fdi/policy/pref.fdi
- synclient
...

Why ? What happen when confs are different ? If I put something in the xorg.conf, it doesn't work well, if I put something in a fdi file, it does nothing. The conf from the two gui are different, but none of them actually is the true config of the pad.

The only way I find to configure the touchpad well is a script (at the end of the post) with all the synclient commands.

I put it in the startup apps, it's nearly ok but I must run it manually after a suspend or a hibernate.
And at each start, I get 
```
TapButton2=3 and TapButton3=2
```when in the script, I run :
```
synclient TapButton2=2
synclient TapButton3=3
```If I want my settings, I must run it manually after each boot.

Isn't there a clean way to configure it properly :confused: ?


synclient script :
```
#!/bin/sh

synclient LeftEdge=51
synclient RightEdge=1229
synclient TopEdge=44
synclient BottomEdge=756
synclient FingerLow=25
synclient FingerHigh=30
synclient FingerPress=256
synclient MaxTapTime=180
synclient MaxTapMove=66
synclient MaxDoubleTapTime=180
synclient SingleTapTimeout=180
synclient ClickTime=100
synclient FastTaps=0
synclient EmulateMidButtonTime=75
synclient EmulateTwoFingerMinZ=281
synclient VertScrollDelta=30
synclient HorizScrollDelta=30
synclient VertEdgeScroll=1
synclient HorizEdgeScroll=1
synclient CornerCoasting=0
synclient VertTwoFingerScroll=1
synclient HorizTwoFingerScroll=1
synclient MinSpeed=0.452
synclient MaxSpeed=0.755
synclient AccelFactor=0.0331345
synclient TrackstickSpeed=40
synclient EdgeMotionMinZ=29
synclient EdgeMotionMaxZ=160
synclient EdgeMotionMinSpeed=1
synclient EdgeMotionMaxSpeed=120
synclient EdgeMotionUseAlways=0
synclient UpDownScrolling=1
synclient LeftRightScrolling=1
synclient UpDownScrollRepeat=1
synclient LeftRightScrollRepeat=1
synclient ScrollButtonRepeat=100
synclient TouchpadOff=0
synclient GuestMouseOff=0
synclient LockedDrags=0
synclient LockedDragTimeout=5000
synclient RTCornerButton=4
synclient RBCornerButton=5
synclient LTCornerButton=0
synclient LBCornerButton=3
synclient TapButton1=1
synclient TapButton2=2
synclient TapButton3=3
synclient ClickFinger1=1
synclient ClickFinger2=2
synclient ClickFinger3=3
synclient CircularScrolling=1
synclient CircScrollDelta=0.1
synclient CircScrollTrigger=8
synclient CircularPad=0
synclient PalmDetect=0
synclient PalmMinWidth=10
synclient PalmMinZ=199
synclient CoastingSpeed=20
# synclient PressureMotionMinZ=29
# synclient PressureMotionMaxZ=160
synclient PressureMotionMinFactor=1
synclient PressureMotionMaxFactor=1
synclient GrabEventDevice=1
```

---

### Post by brucem91 on 2009-11-02
> **slick666 said:**
> Aww it was Sooooooo easy

Go to System -> Preference -> Mouse

Then click on the tab **Touchpad**

Under **Scrolling** select the radio button marked **Two Finger Scrolling**

I also recommend checking the box marked **Enable horizontal scrolling**
I am going to have to second that advice. I am running a MacBook Pro 5,3, and left click, two finger right click, and two finger scrolling (once enabled in the mouse gui settings) worked out of the box. I've been using ubuntu on a macbook since 8.10, and it finally seems to work decently out of the box.

---

### Post by johnystevenson on 2009-11-02
thanks slick666

for some reason i thought i was waiting for a script to solve this!

cheers mate:D

---

### Post by maffix on 2009-11-02
Thanks al lot slick666,
your advice solved the two finger scrolling on a macbook pro 4.1!=D>

---

### Post by gigabytes on 2009-11-02
Ok so it seems it all works out of the box... so someone should edit the wiki page accordingly. I think I'll do that. Thanks :D

---

### Post by mabovo on 2009-11-02
> **volanin said:**
> This new version of the Xorg Synaptics driver must be configured with xinput.
This is my configuration:

```
xinput set-int-prop   appletouch "Synaptics Finger"       32 15 25 300
xinput set-int-prop   appletouch "Synaptics Tap Action"   8 0 0 0 0 0 0 0
xinput set-int-prop   appletouch "Synaptics Click Action" 8 1 2 3
xinput set-float-prop appletouch "Synaptics Move Speed"   0.5 2.5 0.1 40
```

The numbers are explained in the manpage.
The new parameters are explained on page 560, section DEVICE PROPERTIES.

```
$ man synaptics
```

The xinput set-int-prop and set-float-prop are explained by the --help option.

```
$ xinput --help
```

To list your current Synaptics configuration, use:

```
$ xinput list-props appletouch
```

Hope that helps.
:)

Volanin,

How did You set up keyboard for portuguese accentuation ?

Thks.

---

### Post by onetruecathal on 2009-11-13
This is great, thanks!

I'd still recommend people to use the wiki instructions for the touchpad config file, as I found the sensitivity was very poor on my Macbook2.1 before I did so. With two finger scrolling enabled too I'm a happy user!

---

