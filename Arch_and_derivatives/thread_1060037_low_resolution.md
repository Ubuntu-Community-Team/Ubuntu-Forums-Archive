---
title: "low resolution"
date: 2009-02-04
forum: Arch and derivatives
---

### Post by stonecoldjha on 2009-02-04
hi,i have got a 19" acer Al1916W LCD screen.but i am not getting the desired screen resolution(1440x900) and refresh rate(75 Hz).presently,the resolution is 1024x768.i have installed the nvidia drivers with "pacman -S nvidia".i went to preferences>screen resolution,but the highest resolution was 1024x768.

---

### Post by Nepherte on 2009-02-04
Try generating a xorg.conf file with nvidia-xconfig if you haven't already:
```
sudo nvidia-xconfig
```
Then restart X by logging off/on again.

---

### Post by Rumor on 2009-02-04
Alternatively, you can edit your /etc/X11/xorg.conf file and set the resolution you desire yourself. Something like:
```
Section "Screen"
Identifier "Screen0"
Device     "Card0"
Monitor    "Monitor0"
DefaultDepth 24
SubSection "Display"
    Viewport  0 0
    Depth     24
    Modes     "1440x900"
EndSubSection
EndSection

```

---

### Post by gjoellee on 2009-02-04
[http://wiki.archlinux.org/index.php/Xorg#Color_Depth](http://wiki.archlinux.org/index.php/Xorg#Color_Depth)

read Color Depth and Resolution

---

