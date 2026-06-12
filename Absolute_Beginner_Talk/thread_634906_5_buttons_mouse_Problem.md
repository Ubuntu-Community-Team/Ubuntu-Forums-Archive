---
title: "5 buttons mouse Problem"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by efond on 2007-12-08
HEllo 

I am owner of a Trust mouse , model Mi-2500X ,it`s a 5 buttons mouse , but now i can use only 3 of them , the other don`t work properly. It`s for back and forward, placed on the left side of the mouse.

Do you have any idea how to fix ?

---

### Post by shirilover on 2007-12-08
I also have a 5 button mouse w/ scroll wheel.
The following it the section of my /etc/X11/xorg.conf
for using all mouse buttons.
```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option	   "Buttons" "7"
    Option	   "ButtonMapping" "1 2 3 6 7"
    Option         "ZAxisMapping" "4 5"
#   Option         "Emulate3Buttons" "true"
EndSection

```

---

### Post by spiderbatdad on 2007-12-08
found this post:[http://ubuntuforums.org/showthread.php?t=328955](http://ubuntuforums.org/showthread.php?t=328955)
i had seen a very simple guide a week or so ag...if i find it i'll post back

---

### Post by Partyboi2 on 2007-12-08
You can try this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```look for this:
> Section "InputDevice"
    ...
    Driver "mouse"
    ...
    Option "Emulate3Buttons" ...
    Option "ZAxisMapping"    ...
    ...
EndSection
then change it to this:


```
Section "InputDevice"
    ...
    Driver "mouse"
    ...
    Option "Emulate3Buttons" "false"
    Option "Buttons"         "7"
    Option "ButtonMapping"   "1 2 3 6 7"
    Option "ZAxisMapping"    "4 5"
    ...
EndSection
```then restart

---

### Post by CatKiller on 2007-12-08
Really you don't need to restart. You can resart X with a Ctrl-Alt-Backspace.

---

