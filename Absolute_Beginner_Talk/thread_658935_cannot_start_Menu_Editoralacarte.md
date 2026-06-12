---
title: "cannot start Menu Editor/alacarte"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2008-01-05
got a "Starting Main Menu" tab in the panel (bottom) for a few seconds but the Main Menu window did not open. This is the traceback:
```

Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 19, in <module>
    import gtk, gtk.glade, gmenu, gobject, gnomevfs, gnome.ui
ImportError: No module named gnomevfs
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 38, in apport_excepthook
    from apport.fileutils import likely_packaged
ImportError: No module named apport.fileutils

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 19, in <module>
    import gtk, gtk.glade, gmenu, gobject, gnomevfs, gnome.ui
ImportError: No module named gnomevfs

```

---

### Post by gmjs on 2008-01-05
Hi,

I can't decide if this is an Alacarte issue or a Python issue, but let's try the easiest solution first!

Open a terminal window and reinstall Alacarte (the 'Main Menu' app) with the following line:

#  **sudo aptitude reinstall alacarte**

You may need your Ubuntu CD.

Hope this helps,

Graham

---

### Post by oliviacond on 2008-01-06
sorry, it didn't work out

---

