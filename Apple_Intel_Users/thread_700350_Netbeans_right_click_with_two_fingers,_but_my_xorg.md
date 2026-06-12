---
title: "Netbeans right click with two fingers, but my xorg.conf states it must do it with 3!"
date: 2008-02-18
forum: Apple Intel Users
---

### Post by Tasu on 2008-02-18
Hallo, I've setup my xorg.conf to have the right click mapped on three fingers tap, just to be sure that the 2 fingers are used only for scrolling, here is the relevant xorg snippet:
```

Section "InputDevice"
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
        Option "SendCoreEvents" "True"
        Option "Protocol" "auto-dev"
        Option "Device" "/dev/psaux"
        Option "SHMConfig" "True"
        Option "LeftEdge" "100"
        Option "RightEdge" "1120"
        Option "TopEdge" "50"
        Option "BottomEdge" "310"
        Option "MaxTapTime" "150"
        Option "MaxTapMove" "90"
        Option "MaxDoubleTapTime" "180"
        Option "VertScrollDelta" "25"
        Option "HorizScrollDelta" "30"
        Option "HorizEdgeScroll" "0"
        Option "VertEdgeScroll" "0"
        Option "FastTaps" "true"
        Option "TapButton1" "1"
        Option "TapButton3" "3"
        Option "VertTwoFingerScroll" "1"
        Option "HorizTwoFingerScroll" "1"
        Option "AccelFactor" "0.2"
        Option "MinSpeed" "0.4"
        Option "MaxSpeed" "1.5"
        Option "FingerLow" "5"
        Option "FingerHigh" "25"
EndSection

```

Everything works well in all the apps I installed except for NetBeans 6 (installed via the sh I found on the netbeans website), here, if I use the 2 fingers scroll, it both scrolls and opens the right click dialog leading to a not good scroll (if I do the movement fast, I can scroll a bit before the dialog appears), the three fingers tap still works, even in netbeans bringing up the right click dialog.
How could I get rid of that strange mixed behaviour in netbeans when using the two fingers on the pad?

Thanks
Gabriele

---

### Post by cyberdork33 on 2008-02-18
Try specifically disabling two-finger click:
```
Option "TapButton2" "0"
```

---

### Post by Tasu on 2008-02-19
Thanks for the answer! ^_^
Just tried it... ctrl+alt+backspace... fired up netbeans, and... the same behaviour... O_O I'm starting to think that's indeed a swt ... ehrm ... feature!? O_O

---

### Post by cyberdork33 on 2008-02-19
I don't use netbeans myself, but what framework does it run on? I would guess that it runs on java, and in that case, I might suggest that it is an interoperability issue with your javaVM. Xorg seems to be handling things correctly, but netbeans is misinterpreting signals for some reason. Is there some other place that you might be able to configure this for java?

---

### Post by Tasu on 2008-02-19
Well, I'm trying Netbeans as a Ruby on Rails IDE, I heard good things about that, but usually I'm not a great fan of VMs, so I don't really know how to configure Java.... I can say what version is using the netbeans installation, that's the sun-java6-jdk package found in the ubuntu repos (sure about that because even the alternatives configuration show it as the one checked), but I don't really know how to customize the java installation.

O_O

---

