---
title: "Icon problems with Onboard"
date: 2012-06-01
forum: Assistive Technology &amp; Accessibility
---

### Post by perudupinkop on 2012-06-01
Hello guys, 

I recently install Ubuntu 10.10 on a Toshiba Folio 100 Tablet but i can't launch the virtual keyboard "onboard" which is pretty annoying ...

Went I run it form a terminal, I get this error :

```

...
File "/usr/lib/python2.6/dist-packages/Onboard/IconPalette.py", line 93, in __init__
    self.image_pixbuf = icon_theme.load_icon("onboard", 192, 0)
glib.GError : Icon 'onboard' not present in theme

```

Whereas I have the icon 'onboard.svg' in /usr/share/icons/hicolor/scalable/apps

I read here : [https://bugs.launchpad.net/onboard/+bug/538109](https://bugs.launchpad.net/onboard/+bug/538109) 
that some guys solved there problem by updating there icon theme.
So i've tried to update each of my theme with the gtk-update-icon command but I still get the glib.GError with onboard.

The oddest thing is that i just have one icon (the blank sheet) for all my file or directory in the File Manager.  

I thing that there is a probleme with the theme loading. I tried to change theme but it change nothing.

Help please.

---

