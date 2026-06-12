---
title: "error"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by Coop on 2006-10-21
Hello.Wnenever I start my Ubuntu 6.06 the following message comes:

Bug detected
A programming error has been detected.It probably isnt fatal but should be reported to the developers:
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/deskbar/ui/cuemiac/Cuemiac.py", line 667, in on_change_background
    style.bg_pixmap[gtk.STATE_NORMAL] = pixmap
TypeError: can only assign a GdkPixmap or None
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/deskbar/ui/cuemiac/Cuemiac.py", line 667, in on_change_background
    style.bg_pixmap[gtk.STATE_NORMAL] = pixmap
TypeError: can only assign a GdkPixmap or None

What should I do?How do I report this error?How can I stop this message from appearing when my Ubuntu starts?

---

### Post by podunk on 2006-10-21
Did you install the little search bar thingie? Deskbar or something like that. It's a "know bug" and the only way I could make it go away was remove it with synaptic package manager.

---

