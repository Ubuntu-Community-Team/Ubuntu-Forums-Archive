---
title: "my wacom tablet is backwards"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by linux-loser on 2007-10-31
i have a basic graphire wacom tablet.  it works for the most part, meaning i can use it as a mouse and even draw alittle in photoshop 7 with it.  but its upside down, it seems to think that the stylus is the eraser, and i get no pressure sensetivity.  

i know afew people have covered this on the forums already but im still lost on how to do all this.  ive installed the wacom-tools but dont know how to configure them.  

im running x64 fiesty and have a USB wacom... how can i get this working? any help would be great.  

thank you for your time.

---

### Post by ltk5 on 2007-11-01
First restart you session, and see if that helps.
Then check out your xorg.conf if it's configured correctly.

Mine looks like this:
```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
  # Option "PressCurve" "50,0,100,50"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

```

You could also check the linux wacom project.
[http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)

---

