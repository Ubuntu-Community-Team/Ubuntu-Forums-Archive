---
title: "Changing network-manager applet icons"
date: 2009-09-04
forum: Art &amp; Design
---

### Post by steveov on 2009-09-04
Hi! I'm trying to change my nm-applet icon.
I downloaded some .pngs here [http://www.gnome-look.org/content/show.php/NetworkManager+Signal+Icons?content=88706](http://www.gnome-look.org/content/show.php/NetworkManager+Signal+Icons?content=88706) and did a search and replace for nm-signal-*

I've poked around the files and everything seems updated but the old wifi bars are still showing. I tried rebooting, too.

How do I get Gnome to recognize the new icons?

---

### Post by steveov on 2009-09-04
Solved with 
update-gtk-icon-cache /usr/share/icons/hicolor

---

### Post by irate.turtle on 2009-09-11
Doesn't work for me

```
$ update-gtk-icon-cache
bash: update-gtk-icon-cache: command not found
$ apt-cache search update-gtk-icon-cache
$ apt-cache policy update-gtk-icon-cache
W: Unable to locate package update-gtk-icon-cache
$ 

```

---

### Post by Johnny B on 2009-09-30
gtk-update-icon-cache 

[http://library.gnome.org/devel/gtk/unstable/gtk-update-icon-cache.html](http://library.gnome.org/devel/gtk/unstable/gtk-update-icon-cache.html)

---

