---
title: "Python Locale Help"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by gnama on 2007-01-21
How do I set my lc_all and locale? It bugs me alot when I get error messages..:mad:

---

### Post by po0f on 2007-01-21
gnama,

What error messages?  Please post them.

---

### Post by gnama on 2007-01-21
(Point2Play_gui.py:8116): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 44, in ?
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

That is when I try to run cedega or vlc

---

