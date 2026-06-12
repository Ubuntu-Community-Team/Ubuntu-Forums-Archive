---
title: "Changing icons?"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by JGKC9AYC on 2006-06-04
How does one change menu icons?  It seems under Gnome, there's generic icons for bluetooth & I don't like the Firefox icons.
I tried changing the Firefox by downloading a couple of them & trying to move them to the appropriate folder, but that didn't work.
Thanks.

---

### Post by %hMa@?b&lt;C on 2006-06-04
if you are using breezy, type in terminal
```
smeg
```
if dapper
```
alacarte
```

---

### Post by JGKC9AYC on 2006-06-04
[QUOTE=jeffc313]
if dapper
```
alacarte
```[/QUOTE]

Here's what I got:

[I](alacarte:20489): GnomeUI-WARNING **: gnome_icon_entry_gtk_entry deprecated, use changed signal!

(alacarte:20489): GnomeUI-CRITICAL **: gnome_icon_selection_stop_loading: assertion `gis != NULL' failed
/usr/lib/python2.4/site-packages/Alacarte/GnomeDialogHandler.py:234: GtkWarning: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed
  iconButton.set_filename(item.iconPath)
[/I]

When I chose "Browse" under "Properties", it didn't show the 2 .png icons I had saved.

---

