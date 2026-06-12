---
title: "Some programs working incorrectly."
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by gnama on 2006-11-26
I was trying to fix a program so I installed xlibs and python-glide (and some other packages) it didnt fix the program so I reinstalled Ubuntu-Desktop(which it removed). So now I cannot open VLC or edit passwords in Archiver. Help me fix this.

---

### Post by gnama on 2006-11-26
I also get this on mostly all of my gnome apps when I run them.
warrion@warrion-laptop:~$ freeloader
Traceback (most recent call last):
  File "/usr/bin/freeloader", line 24, in ?
    import gtk
  File "/var/lib/python-support/python2.4/gtk-2.0/gtk/__init__.py", line 48, in ?
    from gtk import _gtk
ImportError: /usr/lib/libX11.so.6: undefined symbol: XdmcpWrap

---

### Post by gnama on 2006-11-27
I also get this in gnome-btdownload. Maybe I need to uninstall a python client?
Traceback (most recent call last):
  File "/usr/bin/gnome-btdownload", line 10, in ?
    import gobject, gtk, gtk.glade, gnome, gnome.ui, gconf
  File "/var/lib/python-support/python2.4/gtk-2.0/gtk/__init__.py", line 48, in ?
    from gtk import _gtk
ImportError: /usr/lib/libX11.so.6: undefined symbol: XdmcpWrap

---

### Post by gnama on 2006-11-30
Help would be nice!

---

