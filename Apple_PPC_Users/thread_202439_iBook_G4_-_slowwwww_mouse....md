---
title: "iBook G4 - slowwwww mouse..."
date: 2006-06-23
forum: Apple PPC Users
---

### Post by zachws on 2006-06-23
is there any fix for this... it ruins this new experience pretty much. I finally got ubuntu installed. the installer CAN create a bootstrap partition.

yea the touchpad is incredibly slow, and yes i have searched the forum so it is a recurring problem. does anyone have a solution???

thanks

---

### Post by tidris on 2006-06-23
Have you tried the GUI controls at System -> Preferences -> Mouse to see if they affect the touchpad? On my G3 Powerbook I am able to adjust the touchpad behavior that way.

---

### Post by zachws on 2006-06-23
[QUOTE=tidris]Have you tried the GUI controls at System -> Preferences -> Mouse to see if they affect the touchpad? On my G3 Powerbook I am able to adjust the touchpad behavior that way.[/QUOTE]

yea i did that but it doesn't change. i ran all the updates but have yet to go back into ubuntu. ill just wait to see if anyone has a fix. thanks again, tidris. i cant believe i actually got that installed :).

you need anything???

---

### Post by ibookppc on 2006-06-23
Search harder there is a fix. I have a G4 and had the same prob.

---

### Post by benoitc on 2006-06-24
[QUOTE=ibookppc]Search harder there is a fix. I have a G4 and had the same prob.[/QUOTE]

So what is the fix ? other than using synaptic driver ? Same config of X11 on other ppc distro and my mouse works well without any synaptic driver. If there is other tip, could point to it ? Thanks :)

---

### Post by SteveGeorge on 2006-06-24
I had problems with my powerbook 5,8 (February 2005) which was due to a new appletouch driver and changes to the X driver.  Not sure if this applies to ibooks though.

Focusing on the Synaptics driver you need to configure it to fit what you want.  Here's some things you can do:

a.  Check kernel is detecting synaptics driver
cat /proc/bus/input/devices  #it should say SynPS/2 Synaptics Touchpad

b.  Check X.org is configured
See below

c.  Check driver is loaded by X
grep synaptics /var/log/X.o.org

d.  Use synclient to see parameters
	synclient -m 100
For more information see man synaptics

X Config
--------
You can alter the synaptic drivers configuration within X.  To do this you must enable the the synclient program.  This is a security risk in a multi-user environment as anyone can change parameters - more "inconvenient" because someone can mess up X.  In the InputDevice section of your X.org you have a Synaptics Touchpad bit, add the following option:
    Option  "SHMConfig" "on"
download either qsynaptics or gsynaptics and use this to play with the configuration.

I've played with the parameters a lot and it's OK but not great - I still prefer using my mouse.

---

### Post by zachws on 2006-06-24
i found this: [http://kubuntuforums.net/forums/index.php?topic=5024.new](http://kubuntuforums.net/forums/index.php?topic=5024.new)

but how do i authorize my xorg document? i put in the changes but it wont let me save without the proper credentials. anytime you take a step with this linux stuff you take one back.

---

### Post by dombleu on 2006-06-24
I'm sorry to tell you that this way, but you will need to cope with the permission system in linux. That's the way it's made, and that's why it's safe.

```
sudo gedit /etc/fstab
```

followed by your password should grant you for saving your changes.

---

### Post by hongguang.cui on 2006-06-25
Plz add below codes into /etc/X11/xorg.conf
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
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

in detial, see /usr/share/doc/xserver-xorg-input-synaptics/README.alps

---

### Post by zachws on 2006-06-25
how does your code work vs this one ive copied from an old page and originally used in my xorg.conf?

> Section "InputDevice"
   Identifier "Synaptics Touchpad"
   Driver "synaptics"
   Option "SendCoreEvents" "true"
   Option "Device" "/dev/input/mice"
   Option "Protocol" "auto-dev"
   Option "LeftEdge" "0"
   Option "RightEdge" "850"
   Option "TopEdge" "0"
   Option "BottomEdge" "645"
   Option "MinSpeed" "0.4"
   Option "MaxSpeed" "1"
   Option "AccelFactor" "0.02"
   Option "FingerLow" "55"
   Option "FingerHigh" "60"
   Option "MaxTapMove" "20"
   Option "MaxTapTime" "100"
   Option "HorizScrollDelta" "0"
   Option "VertScrollDelta" "30"
   Option "SHMConfig" "on"
EndSection

---

### Post by miikkee on 2006-06-26
Hi guys... Thanks for the xorg.conf steup. I tried both on my powerbookG4. Zach's proposed code is awfull with my powerbook. Hong's code works pretty well... Just wanted to let you know for the powerbook...

---

### Post by miikkee on 2006-06-26
Actually, not quite perfect... But good enough for now I guess

---

### Post by zachws on 2006-06-27
yes i will second that claim, hongs is much better.

---

