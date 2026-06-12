---
title: "Ubuntu mouse freezing"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by Taren on 2007-01-08
ok i'm having a troble with my ubuntu version 6.06 and it keeps freezing my mouse and my teacher who knows of my problem suggested that i check my video i tried but i didn't know how so can someone tell me how and what to do to fix my problem
specs of my computer i'm running is a dell dimension c521 amd athlon 64 2.4 ghz 1 gb dual ram and ati radeon x1300 256 video card

---

### Post by c-ron on 2007-01-08
what kind of mouse do you have (ps2, usb)?
When you 'cat /etc/X11/xorg.conf' from the console, what does your "InputDevice" Identifier     "Mouse0" section display?

Here's mine:
> Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection


---

### Post by lucky_chouhan on 2007-01-08
look if this modem is serial then problem is most linux distribution or if you have PS/2 mouse then configure your mouse configuration.

---

### Post by moshuptrail on 2007-01-08
Are you by any chance using a synaptics touchpad?

They seem to have some problems freezing.

---

### Post by Taren on 2007-01-09
i'm using dell usb mouse and for a little while i can use my keyboard then that freezes up as well

---

### Post by magicfab on 2007-01-24
A similar problem with the E521 series was fixed by a recent BIOS upgrade from Dell.

See:
[https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellnSeries](https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellnSeries)

---

