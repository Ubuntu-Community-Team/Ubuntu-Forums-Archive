---
title: "cannot launch menu layout"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by mr.digwell on 2007-01-31
hi
maybe i'm just being a stoopid noob, but when i click system/preferences/menu layout, all i get is "starting menu layout..." then nothing. do I have to run as root? if so, how?
hope someone can help.

---

### Post by mikewhatever on 2007-01-31
No, you don't need to run as root. It should just open. Another way of doing it, is right clicking on the menu in the top panel, and choosing Edit Menus. Hope this works.

---

### Post by mr.digwell on 2007-01-31
nope, still no joy. just get "starting menu layout" for about 5 - 10 secs then nothing. damn infuriating.
is there any way i can run it from a command line?

---

### Post by mr.digwell on 2007-01-31
hmmm,
have tried using alacarte, which runs, but adding or changing entries does nothing and gavethis output in terminal:

andy@pingu:~$ sudo alacarte
Password:
/var/lib/python-support/python2.4/gtk-2.0/bonobo/__init__.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/Alacarte/DialogHandler.py", line 441, in on_menu_contents_changed
    self.saveMenu(self.menu_original_values, True)
  File "/usr/lib/python2.4/site-packages/Alacarte/DialogHandler.py", line 463, in saveMenu
    if path == values[0]:
IndexError: tuple index out of range
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/Alacarte/DialogHandler.py", line 441, in on_menu_contents_changed
    self.saveMenu(self.menu_original_values, True)
  File "/usr/lib/python2.4/site-packages/Alacarte/DialogHandler.py", line 463, in saveMenu
    if path == values[0]:
IndexError: tuple index out of range

---

### Post by Buck2348 on 2007-01-31
Have you tried rebooting?

Buck

---

### Post by mr.digwell on 2007-02-01
yes, i have tried rebooting, hitting my head against the wall, & shouting at my laptop very aggressively, all to no avail.

---

### Post by ComplexNumber on 2007-02-01
**mr.digwell**
theres no need for you to run alacarte as root. that just changes roots menu, not yours. what happens when you type in 'alacarte'(WITHOUT sudo)?

---

### Post by mr.digwell on 2007-02-01
i have taken the cowards way out, and reinstalled. "menu layout" now works fine. many thanks to everyone who took the time to help.

---

### Post by Zer0Nin3r on 2007-02-04
Not sure why I cannot create a new menu item.  I'm getting this from the terminal:

> /var/lib/python-support/python2.4/gtk-2.0/bonobo/__init__.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/Alacarte/MainWindow.py", line 281, in on_new_item_button_clicked
    self.editor.createItem(parent, values[0], values[1], values[2], values[3], values[4])
  File "/usr/lib/python2.4/site-packages/Alacarte/MenuEditor.py", line 219, in createItem
    file_id = self.__writeItem(None, icon, name, comment, command, use_term)
  File "/usr/lib/python2.4/site-packages/Alacarte/MenuEditor.py", line 519, in __writeItem
    file_id = util.getUniqueFileId(name, '.desktop')
  File "/usr/lib/python2.4/site-packages/Alacarte/util.py", line 88, in getUniqueFileId
    path = getUserItemPath()
  File "/usr/lib/python2.4/site-packages/Alacarte/util.py", line 156, in getUserItemPath
    os.makedirs(item_dir)
  File "/usr/lib/python2.4/os.py", line 156, in makedirs
    makedirs(head, mode)
  File "/usr/lib/python2.4/os.py", line 159, in makedirs
    mkdir(name, mode)


OSError: [Errno 13] Permission denied: '/home/jigga/.local/share'


**edit**
I just tried to reinstall with no luck.

---

### Post by oliviacond on 2008-02-16
mine was:

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

tried reinstall

---

