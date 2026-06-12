---
title: "Dark Adwaita?"
date: 2011-12-21
forum: Art &amp; Design
---

### Post by lolpenguin on 2011-12-21
For some reason _Totem_ and _Eye of GNOME_ use a "dark" variant of Adwaita. I have checked the theme folders, and parts of this "Dark Adwaita" theme exist, but there is no such theme. Can I use this theme without replacing all the normal files, or is there some way I can make Totem and EoG use the normal Adwaita instead.
Oh, and changing the GTK+ Theme will make their behaviour normal, just the I change it back to Adwaita, they come back to the "dark version".
Any ideads?:confused::confused:
EDIT: I found a complete version of the theme, and it doesn't look too good, now I just need to know how to get Totem and EoG to behave as they should.

---

### Post by prokoudine on 2011-12-21
> **lolpenguin said:**
> now I just need to know how to get Totem and EoG to behave as they should.

*Edit*: as *you* want them to behave, not as they should behave per se :)

You will have to either patch the applications or use themes that do not have dark versions. Those apps use hints for loading dark versions when those are available.

---

### Post by hugmenot on 2012-01-13
Make all apps prefer the dark theme

[QUOTE="$HOME/.config/gtk-3.0/settings.ini"]```
[Settings]
gtk-application-prefer-dark-theme = true
```[/QUOTE]

---

