---
title: "Setting up trackpad tap and scroll on MacBook"
date: 2006-09-15
forum: Apple PPC Users
---

### Post by rscow on 2006-09-15
Has anyone had any success with setting up trackpad tapping and scrolling on their MacBook?  I'd like to get this working on my machine.

Funny thing is, it worked on the LiveCD when I was installing (selecting stuff before the install began).

It just doesn't work out of the box after the install.

Roger

---

### Post by rscow on 2006-09-16
The Gentoo community have a page devoted to installing a dual boot system with OS X and Gentoo Linux. --> [http://gentoo-wiki.com/HARDWARE_Apple_MacBook](http://gentoo-wiki.com/HARDWARE_Apple_MacBook)

Of interest is comments about getting the trackpad to behave like a Synaptics trackpad (BTW WHO makes the one in the MacBook...drivers out there?)
*******************************HERE IT IS******************************
 Input Devices
[edit]
Touchpad in X11

The touchpad works like a champ, just follow the instructions below.

Check your /etc/modules.autoload.d/kernel-2.6 and make sure that you have the following modules loaded (in that order!):

uhci_hcd
evdev
appletouch
usbhid
mousedev

And this goes into your xorg.conf:

Section "InputDevice"
       Identifier      "Synaptics Touchpad"
       Driver          "synaptics"
       Option          "CorePointer"
       Option          "Device"                "/dev/input/mouse1"
       Option          "Protocol"              "auto-dev"
       Option  "LeftEdge"      "100"
       Option  "RightEdge"     "1120"
       Option  "TopEdge"       "50"
       Option  "BottomEdge"    "310"
       Option  "FingerLow"     "25"
       Option  "FingerHigh"    "30"
       Option  "MaxTapTime"    "180"
       Option  "MaxTapMove"    "220"
       Option  "MaxDoubleTapTime"      "180"
       Option  "VertScrollDelta"       "20"
       Option  "HorizScrollDelta"      "50"
       Option  "MinSpeed"      "0.79"
       Option  "MaxSpeed"      "0.88"
       Option  "AccelFactor"   "0.0015"
       Option  "SHMConfig"     "on"
EndSection

This config gives you not only "tap-to-click" but also "two-finger-tap for middle click" and "three-finger-tap for right click"! If you want to switch it so that two-finger-tap is right click and three-finger-tap is middle click, just use

  Option "TapButton2" "3"
  Option "TapButton3" "2"

Vertical/horizontal scrolling is achieved by moving the finger at the right/bottom edge of the pad. You can also activate a "Mac-style" two-finger-scrolling behaviour with

  Option "VertTwoFingerScroll"  "1"
  Option "HorizTwoFingerScroll" "1"

NOTE: I had trouble getting my touchpad to work with the emerged version of synaptics, 0.14.5-r1, so I installed the newest version, 0.14.6, from the developers website. Then I replaced the synaptics_drv.so with the newer one, and now everything works great, including scrolling, two-finger touching, etc... 

*************************************************************************

I didn't have all those modules, though some exist.  I did modify my /etc/X11/xorg.conf file, but no changes took effect on my machine after a restart.

It's a working beginning, though.  Might not work on a deb-based setup, hell, I don't know.  I'm a noob.

Anyone want to take a crack at it?

Roger

---

### Post by rdwtux on 2006-10-31
There's some more information specific to Ubuntu here:

[http://www.jasonparekh.com/linux-on-macbook/](http://www.jasonparekh.com/linux-on-macbook/)

I couldn't get it working on my macbook.  If anyone has success I'd love to hear it.

---

### Post by jasonparekh on 2006-10-31
> **rdwtux said:**
> There's some more information specific to Ubuntu here:

[http://www.jasonparekh.com/linux-on-macbook/](http://www.jasonparekh.com/linux-on-macbook/)

I couldn't get it working on my macbook.  If anyone has success I'd love to hear it.


Which kernel are you running?  If you're on 2.6.17, you will need to apply the Mactel ([www.mactel-linux.org](www.mactel-linux.org)) patches.

I'll post more details on the page in a few days (things are pretty hectic at the moment)

jason

---

### Post by rdwtux on 2006-10-31
> **jasonparekh said:**
> Which kernel are you running?  If you're on 2.6.17, you will need to apply the Mactel ([www.mactel-linux.org](www.mactel-linux.org)) patches.

jason

Thanks for the info.  Yeah I'm on 2.6.17.  I couldn't get it to stop using mousedev no matter what I tried.

Thanks for your help.

---

