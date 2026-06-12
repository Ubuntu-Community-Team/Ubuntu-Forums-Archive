---
title: "Install default Breezy Badger theme on Feisty Fawn"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by kucinghitam on 2007-08-27
is it possible to extract default breezy badger theme from its cd and install it on feisty fawn? for some reason, feisty fawn's human theme doesnt suit my taste and im trying to get the old default theme in breezy badger..where the theme files are kept on cd?

---

### Post by cookies on 2007-08-27
> **kucinghitam said:**
> is it possible to extract default breezy badger theme from its cd and install it on feisty fawn? for some reason, feisty fawn's human theme doesnt suit my taste and im trying to get the old default theme in breezy badger..where the theme files are kept on cd?

The file for Feisty I know are these:
/usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
/usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.la

So maybe for Breezy:
/usr/lib/gtk-VERSION/GNOME-VERSION/engines/libubuntulooks.so
/usr/lib/gtk-VERSION/GNOME-VERSION/engines/libubuntulooks.la

So copy those file to
/usr/lib/gtk-2.0/2.10.0/engines/

And then copy this file /usr/share/themes/Human/gtk-VERSION/gtkrc  to /usr/share/themes/Human/gtk-2.0/gtkrc and /usr/share/themes/Human/metacity-1/metacity-theme-1.xml to /usr/share/themes/Human/metacity-1/

Just my guess.

---

### Post by wolfen69 on 2007-08-27
if that doesnt work, go to [http://www.gnome-look.org/](http://www.gnome-look.org/) and have a look around. there are many themes available.

---

