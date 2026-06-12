---
title: "[Mouse] enable side mouse button"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by ejblom on 2007-11-30
Dear  users,

I've checked many many topics but I can't figure it out. I have a Logitech Mouseman pro. I would like to enable the side button as the back option in Firefox.

There are 5 possible buttons according to xev:

1) left click
2) wheel click
3) right click
4) wheel up
5) wheel down
2) side button

As you can see, the side button doesn't appear to have unique button mapped.
I tried to increase the buttons setting Xorg.conf, didn't work, it staid at button 2.

/etc/X11/xorg.conf output

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Buttons" "5"
    Option         "ZAxisMapping" "4 5"
  # Option         "Emulate3Buttons" "true"
EndSection
```

By playing around with xorg.conf I was able to get back/forwarg being mapped to wheel, but that's not really workable. Anyone have a clue?

---

### Post by doctapeppa on 2007-11-30
Here's mine:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"	"7"
	Option		"ButtonMapping"	"1 2 3 6 7"
EndSection

```

---

### Post by ejblom on 2007-11-30
Thanks man! That works.

---

### Post by blue212 on 2007-12-03
Works perfect!!! Now my back and forward buttons work!!

I am using a Logitech MX518 USB

---

### Post by gwethir on 2007-12-09
When I tried using doctapeppas config, when I restarted my ubuntu couldn't find the graphic card and started in that bad graphic mode. So I had to edit the one I already had, and it works now, here is mine:

```

Section "InputDevice"
    # generated from default and edited by me :D
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" 	"4 5"
    Option	   "Buttons"		"7"
    Option	   "ButtonMapping"	"1 2 3 6 7"
EndSection

```

---

### Post by computernub1 on 2007-12-12
Where would you enter this information? When i enter it in terminal it says:

bash: Section: command not found

---

### Post by furryfrog on 2008-01-14
Not a terminal command.  This should be added/modified in the appropriate section in xorg.conf
in the terminal enter to following:
```
sudo gedit /etc/X11/xorg.conf
```then find where the text looks similar (i.e. Section "Input Device") and make the suggested changes

---

