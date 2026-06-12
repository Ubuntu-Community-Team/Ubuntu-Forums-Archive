---
title: "Strange GTK Error Message"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by AdemoS on 2008-01-31
I keep seeing this message, all over terminals, whenever I open gedit, or other software:

> Gtk-WARNING **: Theme directory scalable/places/22 of theme black-white_2-Vista_big has no size field

I was wondering what it meant and how to fix it.

Thanks for reading.

---

### Post by Blutack on 2008-01-31
Sounds like a scalable icon file (an SVG image) which is missing some metadata telling Gnome how big to scale it, so it is reverting to default.  Unless you are experiencing problems it isn't really an issue, you could file a bug report with whoever you got the icon from (gnome-look.org or whatever).

---

### Post by AdemoS on 2008-01-31
Yeah, that's where I got the set.

Well besides filling a bug report (which will take a while to get noticed, if ever)

Would you know off to fix the metadata by hand? 

Thanks for your help so far.

---

