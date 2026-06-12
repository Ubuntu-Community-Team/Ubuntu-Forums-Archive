---
title: "Bullet-Proof X and mouse problem"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Dapilot1 on 2007-12-07
So I was trying to configure my mouse correctly, MX510, and I followed the directions on [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Logitech_MX510](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Logitech_MX510)

But when I reboot, Bullet-Proof kicks in and says my graphics card is messed up.
That is clearly untrue because when i revert to my back-up the graphics are fine.
I was wondering if anyone knows how to get all the buttons on the MX510 to work because following the guide doesn't work.

Edit: The evdev driver is installed "xserver-xorg-input-evdev is already the newest version."

---

### Post by Crashmaxx on 2007-12-08
If you changed the name of the mouse or anything other then adding the "Driver "evdev"" line then that is probably where your problems are coming from. For example, my mouse is called "Mouse0" and not "Configured Mouse" and changing that will break the config. Revert to the backup and just add that one line. The only other line you may need to add is the "Option "Name" "Logitech MX510"", but try it without that first.

---

### Post by r00tzz on 2007-12-10
I still think evdev is imature. If you boot your comp without the mouse pluged-in, X will be messed up. Tried that a lot of times. I can't do any programing, but I can reproduce the error everytime I try to boot my laptop whitout my mouse.

---

### Post by Dapilot1 on 2007-12-11
Well the name is the same, but I found that this works.
```
 Section "InputDevice"
       Identifier	"Configured Mouse"
       Driver		"mouse"
       Option		"CorePointer"
       Option		"Device"	"/dev/input/mice"
       Option		"Protocol"	"ExplorerPS/2"
       Option		"ZAxisMapping"	"4 5"
       Option		"Buttons"	"7"
       Option		"ButtonMapping"	"1 2 3 6 7"
EndSection 
```

---

