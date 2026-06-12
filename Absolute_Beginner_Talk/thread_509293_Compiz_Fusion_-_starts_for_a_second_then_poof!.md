---
title: "Compiz Fusion - starts for a second then *poof*!"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by eoghanmurray on 2007-07-25
I've just installed Compiz Fusion with XGL in Feisty - BUT... I've set it to launch at startup, and it does, but only for a second, and then it reverts back to Metacity. When I type 'compiz --replace' I get the following in terminal:
```
Backend     : ini
Integration : true
Profile     : default
Adding plugin fakeargb (fakeargb)
Adding plugin mblur (mblur)
Adding plugin splash (splash)
Adding plugin regex (regex)
Adding plugin resizeinfo (resizeinfo)
Adding plugin glib (glib)
Adding plugin text (text)
Adding plugin winrules (winrules)
Adding plugin video (video)
Adding plugin put (put)
Adding plugin water (water)
Adding plugin plane (plane)
Adding plugin bench (bench)
Adding plugin snap (snap)
Adding plugin tile (tile)
Adding plugin resize (resize)
Adding plugin showdesktop (showdesktop)
Adding plugin thumbnail (thumbnail)
Adding plugin scalefilter (scalefilter)
Adding plugin reflex (reflex)
Adding plugin annotate (annotate)
Adding plugin gotovp (gotovp)
Adding plugin expo (expo)
Adding plugin clone (clone)
Adding plugin place (place)
Adding plugin rotate (rotate)
Adding plugin screenshot (screenshot)
Adding plugin crashhandler (crashhandler)
Adding plugin opacify (opacify)
Adding core settings (General Options)
Adding plugin svg (svg)
Adding plugin fs (fs)
Adding plugin snow (snow)
Adding plugin move (move)
Adding plugin cubereflex (cubereflex)
Adding plugin fadedesktop (fadedesktop)
Adding plugin zoom (zoom)
Adding plugin wobbly (wobbly)
Adding plugin imgjpeg (imgjpeg)
Adding plugin trailfocus (trailfocus)
Adding plugin extrawm (extrawm)
Adding plugin animation (animation)
Adding plugin blur (blur)
Adding plugin switcher (switcher)
Adding plugin minimize (minimize)
Adding plugin dbus (dbus)
Adding plugin png (png)
Adding plugin firepaint (firepaint)
Adding plugin decoration (decoration)
Adding plugin fade (fade)
Adding plugin wall (wall)
Adding plugin inotify (inotify)
Adding plugin cube (cube)
Adding plugin group (group)
Adding plugin addhelper (addhelper)
Adding plugin vpswitch (vpswitch)
Adding plugin neg (neg)
Adding plugin scale (scale)
Adding plugin scaleaddon (scaleaddon)
Adding plugin ring (ring)
Initializing core options...done
Initializing mblur options...done
Initializing put options...done
Initializing water options...done
Initializing tile options...done
Initializing resize options...done
Initializing thumbnail options...done
Initializing annotate options...done
Initializing place options...done
Initializing crashhandler options...done
Initializing snow options...done
Initializing move options...done
Initializing zoom options...done
Initializing minimize options...done
Initializing firepaint options...done
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


```

There must be something wrong there. Any solutions? Thanks very much in advance :D

---

### Post by threeonethree on 2007-07-25
libdecoration.so

click update button on top right of screen and update to latest version?

---

### Post by eoghanmurray on 2007-07-25
I've got it running - thanks - but no window borders!

---

### Post by threeonethree on 2007-07-25
try metacity --replace in terminal ?

if that dont work why dont u try installing and using emerald  window decorations?

---

### Post by eoghanmurray on 2007-07-25
I have emerald themes installed - when i type emerald --replace I get:
```
eoghan@eoghan-ubuntufeistyfawn-ultimate-edition-01:~$ emerald --replace
Segmentation fault (core dumped)
```

when i type emerald --replace &, I get:
```
eoghan@eoghan-ubuntufeistyfawn-ultimate-edition-01:~$ emerald --replace &
[1] 7799

```

---

### Post by threeonethree on 2007-07-25
tried METACITY --REPLACE ??

---

### Post by eoghanmurray on 2007-07-25
that's it working now - thanks so much - i overlooked that, sorry :(
but thank you. :D :D :D

---

