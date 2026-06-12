---
title: "Gimp 2.8 crashes on Save"
date: 2013-04-22
forum: Art &amp; Design
---

### Post by BcRich on 2013-04-22
Hi,

I haven't had any problems with GIMP 2.8 in terms of stability until recently.
Everytime I save and image under different name the GIMP crashes with this error message
```
(gimp:9353): Gtk-CRITICAL **: IA__gtk_tree_model_get: assertion `GTK_IS_TREE_MODEL (tree_model)' failed

(script-fu:9363): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error
Segmentation fault (core dumped)


```
Yikes! does anybody know what it means? I don't recall installing anything that could have caused this error :confused:
Ubuntu 12.04 x64, 8GB RAM, AMD hex-core, AMD 6850GPU
the size of the image is also irrelevant, as this happens with 2K or <1K images

---

### Post by BcRich on 2013-04-22
reported bug here [https://bugzilla.gnome.org/show_bug.cgi?id=698603](https://bugzilla.gnome.org/show_bug.cgi?id=698603)

---

### Post by ibjsb4 on 2013-04-22
This isn't much, but I have been searching "script-fu: gimp_wire_read" and found a few suggestions to try.  They range from changing out your theme to checking plugins to xorg to reinstalling.  Doesn't seem to be just one good fix for this.  So here's the link and I wish you good luck.

[https://www.google.com/search?client=ubuntu&channel=fs&q=script-fu%3A+gimp_wire_read&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=script-fu%3A+gimp_wire_read&ie=utf-8&oe=utf-8)

---

### Post by tgalati4 on 2013-04-22
Open gimp in a terminal.  There are several switches that you can use (such as --verbose) to see what is going on.

```
man gimp
```

Let us know what you find.

---

### Post by BcRich on 2013-04-25
The issue was resolved due to a conflict with an accessibility app. see the bug report above.

---

