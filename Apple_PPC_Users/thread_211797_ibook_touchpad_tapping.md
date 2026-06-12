---
title: "ibook touchpad tapping"
date: 2006-07-08
forum: Apple PPC Users
---

### Post by Doug_M on 2006-07-08
Hi, I want the touchpad tapping feature on. Judging by everything I've seen while googling this I realise I am the only person who wants it on, but anyway.

On other distros (gentoo, opensuse, fedora) tapping on the touchpad works out of the box (and doesn't use synclient). With Kubuntu tapping seems disabled.

Here is the relevant xorg.conf part:

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

and it has the right intputdevice line in serverlayout. Looking at the Option lines just now I realise the touchpad should have scrolling ability too, it doesn't.  Any ideas?

Regards,
Doug

---

### Post by gruepig on 2006-07-09
Your xorg.conf looks okay.  Not sure, but ... try the trackpad utility (part of the powerpc-utils package; 'apt-get install powerpc-utils' if you don't have it).  'trackpad show' to see current settings; 'trackpad notap' to disable all tapping events;  'trackpad tap', 'trackpad drag', and 'trackpad lock'  may control the behavior you are looking for.

---

### Post by Doug_M on 2006-07-09
Thanks! That did it!

---

### Post by liam_stoush on 2006-07-25
Thanks also, I've been wondering how to enable tapping for ages.

---

### Post by waldick on 2006-08-07
that worked for me too, but when i restart i have to redo "trackpad tap". i looked in the xorg.conf, but can figure out where to add/change the value.

---

### Post by N8K99 on 2006-08-07
ooh! so happy to have the option to use the trackpad as a click generator!! Must also voice my desire to have this as part of my setup when I reboot - as well as having ksmoothdock running - which file would I add this to in order to make it part of the login process?

---

### Post by hulleye on 2006-08-08
Would like to chime in with the rest. Have been trying to figure out how to set it up so that the trackpad tap is activated automatically every time the computer is restarted.

---

### Post by waldick on 2006-08-09
bump

---

### Post by Xappe on 2006-08-10
when I used breezy on my ibook I think the tapping was enabled after changing something in pbbuttonsd.conf...not really sure though...

---

### Post by waldick on 2006-08-10
i have searched and i can't find where to make the change...our local LUG meets on saturday, maybe smeone there will know...if i find something out i will post it,

j

---

### Post by liam_stoush on 2006-08-11
Hoping to get trackpad tapping working *after* restarts, I've just edited in /etc/pbbuttonsd.conf the line that has:
```
TPMODE = tap
```
Success!

---

### Post by waldick on 2006-08-11
yessssss!

it worked ...thank you

j

---

### Post by gorillajoose on 2006-08-11
for anyone wanting to activate the other trackpad settings:

TPMODE = tap, drag, lock

---

### Post by Motomouse on 2007-09-14
Thanks, this works well for the adb touchpad. I first tried to use psynaptics until i realized my ibook hasn't got a synaptics compatible pad.

---

