---
title: "Background wont stay in fluxbox??"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-09-24
Ive been trying to get a background image in fluxbox but whenever I log off, and back in, the image is gone and the background is back to the default. How do I make the image stay?

---

### Post by oss_monkey on 2006-09-24
Check out the FluxBox HowTo:

[https://help.ubuntu.com/community/Fluxbox#head-2512ece3b39603e80c8e41c3dfc5333d1e3788f5-2](https://help.ubuntu.com/community/Fluxbox#head-2512ece3b39603e80c8e41c3dfc5333d1e3788f5-2)

---

### Post by WalmartSniperLX on 2006-09-24
Thanks :D

---

### Post by WalmartSniperLX on 2006-09-24
Ok i did what it said about uncommenting and correcting the startup script, and the black background is gone (I erased that whole line infact) but Im still not getting my background on the boot. Wtf? lol :confused:  Can anyone help please?

---

### Post by WalmartSniperLX on 2006-09-24
LOL problem solved. I had the wrong command in... :rolleyes:  lol

---

### Post by kerry_s on 2006-09-24
open your /.fluxbox/init file with your text editor, look for this line->
session.screen0.rootCommand:
add this->
session.screen0.rootCommand:	fbsetbg -l

the "-l" sets the last background used

You might find this useful, it's a menu entry to change backgrounds with a simple click. Just add it to your menu->

 [submenu] (Backgrounds)
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]
[end]

---

### Post by WalmartSniperLX on 2006-09-24
> **kerry_s said:**
> open your /.fluxbox/init file with your text editor, look for this line->
session.screen0.rootCommand:
add this->
session.screen0.rootCommand:	fbsetbg -l

the "-l" sets the last background used

You might find this useful, it's a menu entry to change backgrounds with a simple click. Just add it to your menu->

 [submenu] (Backgrounds)
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]
[end]

OMG THAT ENTRY ROCKS! thanks :D

---

