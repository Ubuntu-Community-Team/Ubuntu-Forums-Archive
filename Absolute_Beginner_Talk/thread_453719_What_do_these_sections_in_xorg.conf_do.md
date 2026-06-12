---
title: "What do these sections in xorg.conf do?"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-05-24
Hi, based on another post I commented out the sections of the xorg.conf file listed below.  After restarting computer however kdm would not start and I was booted into console mode.  Currently using Kubuntu Feisty 7.04.  

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

---

### Post by Bachstelze on 2007-05-24
You also need to delete the lines relevant to Wacom devices in your ServerLayout section. If you don't, Xorg expects to find those InputDevice section but doesn't, hence the errors and it not starting.

---

### Post by kevdog on 2007-05-24
What do wacom devices do or what are they??

Side rant --
Why is the xorg.conf file the source of so much frustration??  I needed to jimmy this file when installing Ubuntu a long time ago because the screen was split into three separate sections.  I dont know anything about the X windowing system, but it seems very tempormental and a lot of tweaks need to be made depending on hardware.

---

