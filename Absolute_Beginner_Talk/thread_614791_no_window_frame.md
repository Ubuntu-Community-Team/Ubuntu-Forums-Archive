---
title: "no window frame"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by badguyanil on 2007-11-16
Guys i just saw this and am surprised dono where to go what to do! I dont seem to be getting frames around nautils as in the screenshot. All the other applications like firefox or gedit are fine!!! i have compiz fusion and Emarald installed. Tried switiching the window manager a few times from the compiz fusion icon, but no help :confused: kindly help!

---

### Post by SunnyRabbiera on 2007-11-16
ah, you might of koncked out compiz.
It happens, try logging out of your session and log back in again.

---

### Post by badguyanil on 2007-11-16
> **SunnyRabbiera said:**
> ah, you might of koncked out compiz.
It happens, try logging out of your session and log back in again.

Nope compiz is working fine.... check out this screenshot. Notice awn and firefox working fine with emarald....also can c the window frame in metacity too once that option is chosen from the compiz icon, only for apps. I am not getting the window frame only for nautils.
Screenshot-1--- firefox
Screenshot-2--- ~/Examples
nothing is changed before taking the screenshots!!! i guess i made my point :confused:

---

### Post by atomkarinca on 2007-11-16
try

```
emerald --replace
```

---

### Post by badguyanil on 2007-11-16
> **atomkarinca said:**
> try

```
emerald --replace
```

Tried that too...again works for apps but nautils still does not have the frame !!! this is getting interesting now! :KS

---

### Post by SunnyRabbiera on 2007-11-16
or just turn off the effects.
I know compiz can freak out like this but sometimes if you turn off the effects and put them back on after logout it works okay.

---

### Post by Znort_Ubern00b on 2007-11-16
sudo nvidia-xconfig --add-argb-glx-visuals -d 24


if you have nvidia card copy above text into terminal, it sorted out my problem when i had it.

---

### Post by atomkarinca on 2007-11-16
if you have compiz icon installed, you can try "restart window decorator" or something like that. i admit it's a weird bug. i can understand if it's not working completely but this i have no idea.

---

### Post by badguyanil on 2007-11-16
> **SunnyRabbiera said:**
> or just turn off the effects.
I know compiz can freak out like this but sometimes if you turn off the effects and put them back on after logout it works okay.

lolz... thanks for the great idea but it actually worked!...this reminds me of windows restarts after installing even a browser plugin.. thanks a ton! i have the frame back :)

Thanx to the other guys for helping out too!!!

---

