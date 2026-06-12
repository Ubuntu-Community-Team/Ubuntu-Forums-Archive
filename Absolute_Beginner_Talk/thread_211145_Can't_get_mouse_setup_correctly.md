---
title: "Can't get mouse setup correctly"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by kaje on 2006-07-07
I'm trying to setup my Logitech mx518 mouse, because only half the buttons work. My xorg.conf is setup as:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Device" "/dev/input/event1"
        Option          "name" "Logitech USB-PS/2 Optical Mouse"
EndSection
```


When I try to restart X, I get stuck in a command line prompt with the following info and have to edit my xorg.conf to let me back in:

```
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom : Invalid argument
```

But I can't scroll up to see any other errors that might be occurring. Can anyone help?

---

### Post by sitedesign on 2006-08-05
If you edit xorg then why not just dummy out the wacom lines with a # at the beggining.

Also to scroll up the screen in terminal just hold shift and press pgup/pgdn.

Hope that helps.

Regards Pete

---

