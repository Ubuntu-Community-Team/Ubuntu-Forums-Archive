---
title: "[SOLVED] ugly XMMS menus?!"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-11-30
hi,

the drop down menus look gray and ugle with a nasty font

how can I change it?

sv

---

### Post by hyperair on 2007-11-30
XMMS uses Gtk, as opposed to Gtk2. You need to download some gtk themes, and select them with gtk-theme-switch or gtk-chtheme. They're all available in the repository.

Download and install Gtk themes: sudo apt-get install gtk-engines-*
Download and install gtk-theme-switch: sudo apt-get install gtk-theme-switch
Run gtk-theme-switch: gtk-theme-switch

---

### Post by staticvoid on 2007-11-30
awesome! thanks a ton!

good to know that tid bit of info about gtk and gtk2. do other apps have this  "glich" as well then?

sv

---

### Post by hyperair on 2007-11-30
It's not really a glitch. It's just that the Gtk applications aren't properly themed due to the lack of a theme or engine in the system. Other Gtk applications will have this problem as well. But since you have installed the gtk engines and selected a theme all Gtk apps should have no problems now. You might want to take a look at Audacious. It's basically XMMS, but using Gtk2. I personally prefer it over XMMS. If I'm not mistaken it can also use XMMS plugins.
```
sudo apt-get install audacious
```

Another example of a Gtk app would be Audacity, an audio editing tool.

---

### Post by staticvoid on 2007-11-30
yeah, if I remember right audacity did look really ugly...

sv

btw,I couldn't get the theme working.... i'll try the other switcher

I'll try audauciaus

---

### Post by staticvoid on 2007-11-30
WOW.

goodbye xmms hello audacious!!!

It rocks!! All my themes work too :D

sv

---

