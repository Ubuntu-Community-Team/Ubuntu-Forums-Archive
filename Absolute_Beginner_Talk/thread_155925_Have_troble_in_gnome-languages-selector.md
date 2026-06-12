---
title: "Have troble in gnome-languages-selector"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by mzkapoo on 2006-04-06
I had clicked "System...Administration...Languages Selector" but it didn't show.  Thus I type "gksudo /usr/bin/gnome-languages-selector", error showed that
> Traceback (most recent call last):
  File "/usr/bin/gnome-language-selector", line 5, in ?
    import gtk, gtk.glade
  File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 37, in ?    from _gtk import *
ImportError: /usr/lib/libcairo.so.2: undefined symbol: FT_GlyphSlot_Embolden

Do you have howto fix it? I'd like to add Thai Language.

---

### Post by mzkapoo on 2006-04-06
I forgot to tell you. I do that after having upgrade and I have opened port "Dapper" for downloading "libcairo" for "firefox1.5.0.1-2thai1" in [http://linux.thai.net/apt](http://linux.thai.net/apt) then I closed it by # in /etc/apt/sources.list

---

