---
title: "Can i theme GDM2?"
date: 2009-11-24
forum: Art &amp; Design
---

### Post by LIB53 on 2009-11-24
Is it possible to theme the new GDM? If yes, then how do i theme it, and/or where could i find good reference?

---

### Post by Kreisverkehr on 2009-12-23
First: There are no real gdm2 themes, but you can go to the directory /usr/share/images/xsplash there you can change the Wallpaper that is used.
Or try searching for "xsplash" on gnome-look.org to find image packs for xsplash.
furthermore there is a way to change the gtk-theme that is used, but i can't tell how this is done, try google ;)

Hope this helped and was not too late :)

---

### Post by Tibuda on 2009-12-23
yes, it uses gtk+ themes and wallpapers.

to tweak it, run:
```
gksu -u gdm dbus-launch gnome-appearance-properties
```

---

### Post by Psumi on 2009-12-24
> **danielrmt said:**
> yes, it uses gtk+ themes and wallpapers.

to tweak it, run:
```
gksu -u gdm dbus-launch gnome-appearance-properties
```

Why does this open two accessibility option icons in the systray? :| And keep one in the systray after I logout/in?

---

### Post by alexandrius on 2010-08-12
> **Psumi said:**
> Why does this open two accessibility option icons in the systray? :| And keep one in the systray after I logout/in?

aaagr, the same happend to me i have no idea how to remove that **** :(
anyone?

---

### Post by alexandrius on 2010-08-12
i found fix, go to keyboard preferences->accessubukuty tab and uncheck "Accessibility featuras can be toggled with keyboard shortcuts"

---

