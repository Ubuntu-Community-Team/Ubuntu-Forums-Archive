---
title: "Army Ops graghics/display problem?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by tcrosby86 on 2007-07-22
```
timmy@UbuntuBook:~$ armyops
Cheat protection disabled
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
*********************************WARN_ONCE*********************************
File radeon_mm.c function radeon_mm_alloc line 216
Ran out of GART memory (for 1048576)!
Please consider adjusting GARTSize option.
***************************************************************************
Error: Could not get dma buffer... exiting
```


any ideas? im a newb so speak easy please... i searched and didnt find a problem quite like mine...

---

### Post by sad_iq on 2007-07-22
Ok...you have to manually input your GART memory! Type in a terminal ```
sudo nano /etc/X11/xorg.conf
``` look for this section: ```
Section "Device"
Identifier "Ati... "# The name of your card should be here
Driver "radeon"
Option "RenderAccel" "true"
EndSection
```
 And put **Option "GARTSize" "128"** replace 128 with the amount of ram your video card has.The above section should be like this: ```
Section "Device"
Identifier "Ati... "# The name of your card should be here
Driver "radeon"
Option "RenderAccel" "true"
[COLOR="Magenta"]Option "GARTSize" "128"[/COLOR]
EndSection

```
Hope it helps...if not give more feedback...like what card you have and what driver you're using!!

---

### Post by tcrosby86 on 2007-07-22
```
Section "Device"
        Identifier      "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
        Driver          "ati"
        Option          "GARTSize" "128"
        BusID           "PCI:1:0:0"

```

thats what i did do i need to put that other option you had in there as well? how do i save/exit that thin in the terminal?

---

### Post by sad_iq on 2007-07-22
> **tcrosby86 said:**
> do i need to put that other option you had in there as well? how do i save/exit that thin in the terminal?
 It shouldn't hurt ...You save by pressing CTRL+X then Enter then Enter again!!!

---

