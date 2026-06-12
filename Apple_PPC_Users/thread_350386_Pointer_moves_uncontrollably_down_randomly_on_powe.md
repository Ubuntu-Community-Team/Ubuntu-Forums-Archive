---
title: "Pointer moves uncontrollably down randomly on powerbook"
date: 2007-01-31
forum: Apple PPC Users
---

### Post by bifter on 2007-01-31
I've had a problem occur a few times. I have Ubuntu 6.10 on a 12" powerbook g4.

After a period of use the mouse pointer suddenly moves uncontrollably down. As I attempt to move it up it just goes straight down again making it impossible to do anything except hold down the power key for a reboot.

It seems to happen randomly,. Sometimes I can use my G4 for hours with no problems.

Has anyone else had this problem? It never happened when OSX was on the machine making me think it is not a hardware issue.

---

### Post by tcuzela on 2007-02-02
That almost sounds like the trackpad needs to be reset.  Take the lower part of your palm and cover most all of the trackpad.  Hold it there for several seconds (5 is a nice number) and in one smooth motion slide it all the way off to the left or right.  You may want to try this once or twice just to make sure it resets.  I know it helps in Tiger when the pad acts up, hope it will for you too!

---

### Post by dombleu on 2007-02-05
If you want to reconfigure your mouse.... I do have a powerbook 12" G4 and that's the /etc/X11/xorg.conf section for the touchpad that has been working for me:

Section "InputDevice"
   Identifier "Synaptics Touchpad"
   Driver "synaptics"
   Option "SendCoreEvents" "true"
   Option "Device" "/dev/input/mice"
   Option "Protocol" "auto-dev"
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
  Option          "HorizScrollDelta"      "0"
   Option          "MinSpeed"              "0.2"
   Option          "MaxSpeed"              "1.5"
   Option          "AccelFactor"           "0.1"
  Option          "EdgeMotionMinSpeed"    "200"
  Option          "EdgeMotionMaxSpeed"    "200"
  Option          "UpDownScrolling"       "1"
  Option          "CircularScrolling"     "1"
  Option          "CircScrollDelta"       "0.1"
  Option          "CircScrollTrigger"     "2"
  Option          "SHMConfig"             "on"
EndSection

Hope it helps..

Dom

---

