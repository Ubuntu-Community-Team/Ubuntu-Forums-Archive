---
title: "center wall paper in Fluxbox / Blackbox"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by noob_Lance on 2005-12-24
like the title says... how can i do this??

~Lance

---

### Post by firehead on 2006-01-18
i guess it depends on how you set the wallpaper...i.e. what program you use...?

---

### Post by fuscia on 2006-01-18
i think it's fbsetbg -c (or, -center) and then the file name, enter. if you reboot, or login again, you'd have to reset the wallpaper (i don't know how to make it permanent). it's been a while since i used fluxbox. i use feh to set backgrounds in openbox and flwm. i think you can get feh from synaptic.

---

### Post by firehead on 2006-01-18
[QUOTE=fuscia]i think it's fbsetbg -c (or, -center) and then the file name, enter. [/QUOTE]
that's right, if you're using fbsetbg to set your wallpaper
to load your preferred wallpaper at startup there are different ways,probably the easiest one is to edit the style file (see /usr/share/fluxbox/styles) and add (or edit) this line
```
rootCommand:   Esetroot -center  /path/to/your/wallpaper
```
right after the title section...

---

