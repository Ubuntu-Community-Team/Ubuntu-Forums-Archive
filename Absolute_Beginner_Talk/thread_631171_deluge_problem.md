---
title: "deluge problem"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Carl_Barks on 2007-12-04
my deluge was working absolutely fine but when i tried to open deluge yesterday it started, then paused and it stopped there. Since then i haven't managed to make it start.
every time i get that screen : [http://img521.imageshack.us/my.php?image=screenshotjs0.png](http://img521.imageshack.us/my.php?image=screenshotjs0.png)

btw i have the latest version installed.

---

### Post by vishzilla on 2007-12-04
Run 'deluge' in the terminal and post the outcome

---

### Post by Carl_Barks on 2007-12-04
omg : x
after posting the thread it started!1 out of the blue :p
The power of the ubuntu forums?!

and the little window that i couldn't see and it;s black on the image i uploaded, now is visible and is a notification about upgrading to the latest version. after i click yes, i get the error page saying that the latest .deb package is already installed, then why do I get the message about the new version?

God knows ... computers - strange beings

---

### Post by vishzilla on 2007-12-04
try reinstalling deluge, if it happens in future

---

### Post by Carl_Barks on 2007-12-04
f*ck. it did it again.
the problem i could see through terminal while it crushed again is :

Xlib: unexpected async reply (sequence 0xda0)!

also i figured these too :

/var/lib/python-support/python2.5/deluge/interface.py:1019: GtkWarning: gdk_window_set_geometry_hints: assertion `GDK_IS_WINDOW (window)' failed
  gtk.main()
/var/lib/python-support/python2.5/deluge/interface.py:1019: GtkWarning: gdk_window_resize: assertion `GDK_IS_WINDOW (window)' failed
  gtk.main()

---

### Post by koleoptero on 2007-12-04
If by chance it works again go to Edit --> Preferences, and there to the tab Other and deselect "be alerted about new releases"

---

### Post by Trebaruna on 2007-12-04
Do you have the version in the Ubuntu repositories? If so, try getting it manually from deluge-torrent.org

Deluge is still in development, and progressing rapidly: new versions on their site contain a host of new features and fixes. Of course, the one in the repository is supported by Ubuntu, but since it is clearly being troublesome...

---

