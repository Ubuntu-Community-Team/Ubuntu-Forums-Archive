---
title: "scroll on mouse wont work"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by taseal on 2005-09-22
I have a logitech optical mouse with the scroll but it wont work :(

the scroll button works, but it wont go up or down

help pls :(

---

### Post by xmastree on 2005-09-22
Take a look at your /etc/X11/xorg.conf file In particular, the "ZAxisMapping" setting.

Here's mine, for my usb Logitech mouse:```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
```

---

### Post by taseal on 2005-09-22
[QUOTE=xmastree]Take a look at your /etc/X11/xorg.conf file In particular, the "ZAxisMapping" setting.

Here's mine, for my usb Logitech mouse:```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
```[/QUOTE]

that file is read only... how do i write over it? (teghre is a way to make a backup or something i think?)

mine says 

```
    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "PS/2"
    Option "Device"     "/dev/psaux"

```

---

### Post by drogoh on 2005-09-22
[QUOTE=taseal]that file is read only... how do i write over it? (teghre is a way to make a backup or something i think?)

[/QUOTE]

Open it using: sudo gedit

Gedit, by default, will make a backup when you save. (at least mine has when I've used it)

---

### Post by taseal on 2005-09-22
[QUOTE=drogoh]Open it using: sudo gedit

Gedit, by default, will make a backup when you save. (at least mine has when I've used it)[/QUOTE]

ok i figured out how to back it up

how do i restart x withtout restarting ubuntu

it was like sudo killall gnu
sudo gnu

i forget what that gnu thing was... was it gdi ? gni?  lol

---

### Post by xmastree on 2005-09-23
[QUOTE=taseal]it was like sudo killall gnu[/quote]sudo killall **gdm** gnome desktop manager

Although ctrl-alt-backspace is easier.

---

