---
title: "MacOS style tracking"
date: 2006-11-19
forum: Apple PPC Users
---

### Post by Twinaxx on 2006-11-19
I'm running 6.10 Edgy on a Titanium PowerBook G4, 400MHz, with both KDE and Gnome. 

I have pretty much been able to configure it the way I want it, thanks to these forums, except for one thing: trackpad acceleration. 

I really like the way OS X does it, basing cursor distrance travelled on speed, as opposed to Windows, which is a symmetric representation of distance travelled, regardless of how fast your movement is. 

I'm not sure if this can be done, but any pointers (no pun intended) would be greatly appreciated.

---

### Post by applemacmad on 2006-11-20
I have to agree, Mac does have the best Tocuhpad drivers around.
I have been playing with my xorg.conf and I have got it pretty close, but not perfect. If you want, I can post it.
But if anyone feels they have it spot on - please post!!

---

### Post by Twinaxx on 2006-11-20
this is what i mean. tracking accelerates exponentially based on speed. yeah, i'd love to see the xorg.conf.

---

### Post by applemacmad on 2006-11-21
Ok, here's my xorg.conf for the synaptics touchpad.
As I said, it's not perfect. Also, my touchpad (PBG4) may be slightly different from yours. I find that changing 'AccelFactor' and the 'Min/MaxSpeed' has the most effect on it.

```
 Identifier "Synaptics Touchpad"
 Driver "synaptics"
 Option "SendCoreEvents" "true"
 Option "Device" "/dev/psaux"
 Option "Protocol" "auto-dev"
 Option "SHMConfig" "true"
 Option "MinSpeed" "0.25"
 Option "MaxSpeed" "1.35"
 Option "EdgeMotionMinSpeed" "200"
 Option "EdgeMotionMaxSpeed" "200"
 Option "FastTaps" "0"
 Option "MaxTapTime" "0"
 Option "AccelFactor" "0.027"
 Option "HorizScrollDelta" "0"
 Option "FingerLow" "1"
 Option "FingerHigh" "3"
 Option "LeftEdge" "80"
 Option "TopEdge" "80"
 Option "RightEdge" "850"
 Option "BottomEdge" "560"
 Option "TapButton1" "1"
 Option "TapButton2" "3"
 Option "TapButton3" "2"
EndSection

```

---

