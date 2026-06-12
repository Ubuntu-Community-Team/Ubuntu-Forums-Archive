---
title: "Apple Mighty Mouse - thousends of clicks"
date: 2008-12-22
forum: Apple Hardware Users
---

### Post by alfanick on 2008-12-22
Hi all!
I have problem with Apple Mighty Mouse (wired). My xorg.conf:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver "evdev"
	Option "Device" "/dev/input/by-id/usb-Primax_Electronics_Apple_Optical_USB_Mouse-event-mouse"
#	Option "Dev Phys" "usb-*/input0"
	Option "CorePointer"
#	Option "Dev Name" "Primax Electronics Apple Optical USB Mouse"
	Option "RelHWHEELMapTo" "Buttons 7 6"
	Option "Buttons" "8"
	Option "Buttons" "9"
EndSection

```
The problem is that when I'm pressing button (no matter which) it's making a lot of clicks - there should be one click. I'm unable to move windows - they maximize, select text - it's selecting word, line, all, word, all, line... 
xinput test "Configured Mouse"
```

button press   1
button press   1
button press   1
button press   1
button press   1
button press   1
button press   1
button press   1
button press   1
button press   1
button press   1
button press   1
button press   1
button press   1
button press   1
button press   1
button press   1
....

button press   1
button press   1
button release 1

```
Did somebody know response to my problem? :confused:

---

### Post by alfanick on 2008-12-23
Solved! I patched source code to prevent this.

---

### Post by cyberdork33 on 2008-12-24
> **alfanick said:**
> Solved! I patched source code to prevent this.
Mind posting the patch?

If you make a bug report and attach the patch, it will likely be integrated into the distro.

---

