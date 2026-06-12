---
title: "Adding mid-mouse scrolling"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by CrazyArcher on 2008-02-14
Hello

I've recently installed Ubuntu and I miss one nice Win feature - having the window contents scroll while holding the middle mouse button and moving the mouse. How can I get that? Regular scrolling works fine, but I need heavier guns for bigger documents... ;)

---

### Post by neurostu on 2008-02-14
Fist back up your xorg.conf 
```

$sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp

```

Edit /etc/X11/xorg.conf and look for the section "InputDevice" and Identifier "Configured Mouse" then edit it to look like this.


```

Section "InputDevice"
  Identifier	"Configured Mouse"
  Driver	"mouse"
  Option	"CorePointer"
  Option        "Device" "/dev/input/mice"
  Option	"Protocol"	     "ImPS/2"
  Option	"ZAxisMapping"	     "4 5"
  Option	"Emulate3Buttons"    "true"
  Option	"EmulateWheel"	     "on"
  Option	"EmulateWheelButton" "2"
  Option	"YAxisMapping" 	     "4 5"
  Option	"XAxisMapping"	     "6 7"
EndSection

```

---

### Post by CrazyArcher on 2008-02-15
Thank you for response.
It all went good till I tried to save the file - it said "The document could not be saved, as it was not possible to write to file:///etc/X11/xorg.conf.
Check that you have write access to this file or that enough disk space is available." For sure I have enough space... How can I solve it?

---

### Post by neurostu on 2008-02-15
/etc/X11/xorg.conf is a system file and as such it can only be edited by root.
So to edit this file you must use sudo, try:
```

$ sudo gedit /etc/X11/xorg.conf
            or
$ sudo nano /etc/X11/xorg.conf

```
Gedit and Nano are both text editors, Gedit is graphically based where as nano is purley commandline stuff.  If you haven't used nano before I would recommend Gedit.

---

### Post by CrazyArcher on 2008-02-15
Thank you for your time

I edited the file, but it doesn't seem to work. Moreover, Opera responds with an error message ('Illegal URL'). Any ideas?

---

### Post by neurostu on 2008-02-16
Sorry that is how I got it to work for me... I wish I knew more... :-(

---

