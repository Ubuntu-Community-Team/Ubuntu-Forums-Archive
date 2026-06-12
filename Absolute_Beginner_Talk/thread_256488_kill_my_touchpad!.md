---
title: "kill my touchpad!"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by kansaibear on 2006-09-13
breezy 5.10 fresh install on wallstreet (sonnet 500 G3 card)

Cant type cause the touchpad is clickable by default... Need to turn off the click!!

Tried:
[http://ubuntuforums.org/showthread.php?p=476349](http://ubuntuforums.org/showthread.php?p=476349)

But I am lost in syntax... right at the start, 'unpack and in the same directroy'.. .what directory?? tried to cd everywhere but keep ending up with no such file or command or some such error message.

Got synaptics-0.14.6 on my desktop cause that is what it said I needed.

What is the easiest way to kill the click function on my touchpad??

Barry
thought I was smart, then I installed linux

---

### Post by hw-tph on 2006-09-13
Back up your /etc/X11/xorg.conf file and open it in your favourite text editor (gedit, vim, nano, whatever). Find the Synaptics input device. The section may or may not look like this - it have zillions of options enabled:```
Section "InputDevice"
    Identifier  "Synaptics Touchpad"
    Driver      "synaptics"
    Option      "SendCoreEvents"    "true"
    Option      "Device"        "/dev/psaux"
    Option      "Protocol"      "auto-dev"
    Option      "HorizScrollDelta"  "0"
EndSection
```

On the line *before* EndSection, add this:```
    Option      "MaxTapTime"    "0"
```

It should look something like this:```
....
    Option      "HorizScrollDelta"  "0"
    Option      "MaxTapTime"    "0"
EndSection
```

Log out of Gnome and restart GDM - At the GDM login prompt hit Ctrl+Alt+F1 for a console, log in and type **sudo /etc/init.d/gdm restart**.


Håkan

---

### Post by kansaibear on 2006-09-13
thanks for the reply, I had already edited the xorg.conf file with the:
 Option      "MaxTapTime"    "0"
Checked it be sure that it was saved, yup it was.

that was why I downloaded the latest synaptics driver cause I thought that maybe the earlier one didnt have that option...

on a note, ctrl alt f1 had no effect
!
I restarted X11 with ctrl delete

next idea please, still got my cursor jumping all over and making things a real bitch....

---

