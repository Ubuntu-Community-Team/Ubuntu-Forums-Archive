---
title: "Mouse and Apple remote not working after upgrade"
date: 2008-04-29
forum: Apple Hardware Users
---

### Post by Ilove2023 on 2008-04-29
Hello,


I just upgrade to Hardy and I'm facing some troubles... Without changing anything in my configuration after the upgrade, my external mouse has stopped working. Same with the apple remote...

This is the relevant section of my xorg.conf
```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice 	"Synaptics Touchpad" "CorePointer"
	InputDevice	"Configured Mouse" "AlwaysCore"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
#	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

#TRACKPAD
Section "InputDevice"
	Identifier 	"Synaptics Touchpad"
	Driver 		"synaptics"
	Option 		"CorePointer"
	Option 		"Device" "/dev/input/mouse1"
	Option 		"Protocol" "auto-dev"
        [...options...]
	Option		"SHMConfig" "on"
EndSection


```
Note I get some output when I click the mouse on /dev/input/mouse1, but when I use it in the config file, it doesn't change anything.


Concerning the remote control not working, I just have no clue how to test it... It worked out of the box in Feisty already.. ?!

Does anyone know what change happended in this new version?

Thanks in advance!

---

### Post by cyberdork33 on 2008-04-29
> **Ilove2023 said:**
> Without changing anything in my configuration after the upgrade...
that may be your issue... Xorg has undergone many, many changes, and most of the config options are not even needed anymore.

---

### Post by Ilove2023 on 2008-04-29
Arf, should I do a dpkg-reconfigure of the xserver package then?

Any clue concerning the remote? If I'm not wrong this is not related with Xorg?!

---

### Post by cyberdork33 on 2008-04-29
> **Ilove2023 said:**
> Arf, should I do a dpkg-reconfigure of the xserver package then?

Any clue concerning the remote? If I'm not wrong this is not related with Xorg?!yea, backup your config (just in case theres something you still need) and do ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

I don't know about the remote, I haven't even tried to use it in hardy yet.

---

