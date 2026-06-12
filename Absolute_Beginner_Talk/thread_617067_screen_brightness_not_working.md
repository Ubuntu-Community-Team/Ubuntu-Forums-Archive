---
title: "screen brightness not working"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by dracker on 2007-11-18
Ubuntu Gutsy works almost perfectly on my Gateway MX6448, one of the things that's not working is screen brightness, once in ubuntu (every since the usplash screen) the Fn + Up/Down combination doesn't work to adjust my brightness, I have other button to make it go all the way up and all the way down and that is working.
Anyway, this buttons do their job in BIOS and Grub, they even work in the gparted live cd, but no Ubuntu... , also the brightness control that goes in the panel doesn't work.
My card is Ati Radeon Xpress 1100, I'm using the restricted driver (The one that's the default in Gutsy).
Running the fglrxinfo command I get this:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)

So please help me find the solution for this :confused:

---

### Post by stido on 2007-11-19
in most laptops, some Fn+<X> function keys are transferred from BIOS to the OS after completing the boot process. but the OS needs the correct drivers in order to respond to those Fn keys. unfortunately, most manufacturers only provide Windows drivers. 

you could also try Google around for drivers made by opensource people outside Gateway. maybe yours might turn up somewhere.

---

### Post by dracker on 2007-11-20
What driver is the responsible for this? :-k

---

