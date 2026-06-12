---
title: "Problem with Serial Mouse (it moves tooo quickly!!)"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by dupa on 2007-06-12
Hello, i have an old pc with a PS/2 port, but I use on that pc a "Serial Mouse", by default the serial mouse doesn't work, so I have a found a post on  a forum where it is explained to configure in this way:


```
Section "InputDevice"
Identifier "Serial Mouse"
Driver "mouse"
Option "Protocol" "Microsoft"
Option "Device" "/dev/ttyS0"
Option "SendCoreEvents" "true"
Option "Emulate3Buttons" "true"
Option "Emulate3Timeout" "70"
EndSection
```



```
#InputDevice "Configured Mouse"
InputDevice "Serial Mouse" "SendCoreEvents"
```

Now the serial mouse works.. but I have two problems:

1) it moves absolutely too quickly!!! i tryed to change the speed in the gnome administration tool.. but it's still incredibly quick..

2) when X starts.. it locks on a black screen.. and only if I move the mouse it appears the graphic login screen..

So I suppose there is still something wrong in my config.

Thanks

---

### Post by arvevans on 2007-06-12
On menus, go to System, Preferences, Mouse, Motion...and set the speed, sensitivity, etc. to what you need.
_._

---

### Post by arvevans on 2007-06-12
Also:

On a terminal screen, do "stty </dev/ttyS0".
If not set to 9600 baud, then do "sudo stty 9600 </dev/ttyS0".

This sets your serial port to the proper speed for using a serial mouse.
_._

---

