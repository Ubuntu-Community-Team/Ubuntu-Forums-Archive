---
title: "Missing Rhythmbox volume icon"
date: 2005-12-05
forum: Bug Reports / Support
---

### Post by sjmorgan on 2005-12-05
The 0.9.1 buils of Rhytmbox seems to be missing the volume control icon. Screenshot attached.

---

### Post by Sutekh on 2005-12-05
[QUOTE=sjmorgan]The 0.9.1 buils of Rhytmbox seems to be missing the volume control icon. Screenshot attached.[/QUOTE]

What's the theme your are using?  I would suggest trying another theme (perhaps a default theme like Human) and see if it returns.

---

### Post by hav0x on 2005-12-05
yeah.
'tis probably a theme issue, my volume icon appears as usual.

---

### Post by Sutekh on 2005-12-05
Just wondering if that little box where the volume should be responds when clicked...

---

### Post by sjmorgan on 2005-12-11
Problem still exists with default theme. Box does repond when clicked.

---

### Post by sjmorgan on 2005-12-11
I am assuming this is because I'm using IceWM as opposed to GNOME.

```

(gdb) n
601	  buf = gtk_icon_theme_load_icon (button->theme, s, w, 0, NULL);
(gdb) n
602	  gtk_image_set_from_pixbuf (GTK_IMAGE (button->image), buf);
(gdb) p buf
$6 = (GdkPixbuf *) 0x0

```

---

### Post by ssam on 2005-12-11
i get this but assumed it was because i was forwarding rhythmbox through a ssh tunnel from a machine without X installed.

you could try running volume-settings-daemon thats will make gtk apps look pretty when you are not running gnome.

---

### Post by sjmorgan on 2005-12-11
[QUOTE=ssam]i get this but assumed it was because i was forwarding rhythmbox through a ssh tunnel from a machine without X installed.

you could try running volume-settings-daemon thats will make gtk apps look pretty when you are not running gnome.[/QUOTE]
```

You have searched for volume-settings-daemon in breezy, architecture i386.
Can't find that file, at least not in that distribution and on that architecture.

```

---

