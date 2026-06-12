---
title: "[SOLVED] Windows can't move around desktop"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by pcostanza on 2007-10-31
Not sure exactly what I did but as I'm learning what can be done with the desktop I obviously screwed up.  When I open anything, the windows don't allow me to move them.  I can use the File, Edit, etc. to shut them down but I can't move them anywhere.  I have compizconfig installed and wobbly windows was working but now....nothing.  What the heck did I do and how do I get it back?

---

### Post by Pumalite on 2007-10-31
Start by disabling special Desktop Effects. And let's see.

---

### Post by Billy_McBong on 2007-10-31
[COLOR="Blue"]try opening the terminal and entering
```
compiz --replace
```
that will restart compiz fusion

and if it still doesn't work you can try using metacity instead of compiz
```
metacity --replace
```[/COLOR]

---

### Post by SunnyRabbiera on 2007-10-31
you might have messed up the engine a bit, to get things back to working condition is to go to
system then to preferences, then click on "appearance"
after the appearance settings window comes up go to the "visual effects" tab and click on the circle that says "none:" next to it
this might work

---

### Post by pcostanza on 2007-10-31
Thanks all.  It seems that it was due to 'Snapping Effects' being enabled but I know I didn't do this on purpose.  Starting over is what fixed this.
Dang, you guys are good and quick. :guitar:

---

### Post by SunnyRabbiera on 2007-10-31
Yeh, just be careful with desktop effects especially if you have lower specs,

---

### Post by rundee_f on 2007-10-31
Open CompizConfig Settings Manager > Window Decoration > in Command line type **emerald** (if ure using emerald) or **gtk-window-decorator** (for standard use)..

---

