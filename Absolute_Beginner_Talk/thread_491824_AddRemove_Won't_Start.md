---
title: "Add/Remove Won't Start"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by fattom23 on 2007-07-04
When I use the Add/Remove icon in the Applications menu, it attempts to start up, goes through the dependency check and even checks the installed packages.  However, when the status bar finishes filling up, the application immediately closes.  Anyone out there have any ideas about why this might be?  Synaptic still works fine, so if I knew the name of the package that controls the Add/Remove programs, I could probably just reinstall it and everything would be groovy.  Any help you can offer would be greatly appreciated.  Thanks!

---

### Post by RomeReactor on 2007-07-04
Hi. That's **gnome-app-install**. Just a warning though: if you mark it for removal, it will tell you it will remove **ubuntu-desktop** with it. ubuntu-desktop is a metapackage containing information about what applications to install with it; in itself it's just an empty package, though it's useful during system upgrades. On the other hand, you can also try running **gnome-app-install** in the terminal (Applications->Accessories->Terminal):
```
gnome-app-install
```
If ti crashes, it will probably leave messages there which can give us a hint as to what is wrong.

---

### Post by fattom23 on 2007-07-04
I ran the program from the command line, and got the following output:

Introspect error: The name org.freedesktop.AppInstall was not provided by any .service files
no listening object (The name org.freedesktop.AppInstall was not provided by any .service files)

** (gnome-app-install:6978): WARNING **: return value of custom widget handler was not a GtkWidget
Got non-package menu entry kiso.desktop
Got non-package menu entry xchm.desktop
Got non-package menu entry k3dsurf.desktop
Got non-package menu entry grdesktop.desktop
Got non-package menu entry tsclient.desktop
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 40, in ?
    app = AppInstall(datadir, desktopdir, sys.argv)
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 171, in __init__
    self.updateCache()
  File "/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py", line 667, in updateCache
    progress)
  File "/usr/lib/python2.4/site-packages/AppInstall/Menu.py", line 124, in __init__
    self.refresh(progress)
  File "/usr/lib/python2.4/site-packages/AppInstall/Menu.py", line 288, in refresh
    self._populateFromEntry(menu, progress=progress)
  File "/usr/lib/python2.4/site-packages/AppInstall/Menu.py", line 354, in _populateFromEntry
    self._populateFromEntry(entry, item,  progress=progress)
  File "/usr/lib/python2.4/site-packages/AppInstall/Menu.py", line 410, in _populateFromEntry
    item.mime = entry.DesktopEntry.getMimeType()
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 74, in getMimeType
    return self.get('MimeType', list=True, type="regex")
  File "/usr/lib/python2.4/site-packages/xdg/IniFile.py", line 129, in get
    value = re.compile(value)
  File "/usr/lib/python2.4/sre.py", line 180, in compile
    return _compile(pattern, flags)
  File "/usr/lib/python2.4/sre.py", line 227, in _compile
    raise error, v # invalid expression
sre_constants.error: multiple repeat

I have no idea what all that means, though!  Hopefully it means something to someone out there!  Thanks.

---

### Post by RomeReactor on 2007-07-04
Hmmmm... This really is beyond my grasp. Did you install KDE and then uninstall it? Just a thought. Also look in Synaptic to see if **gnome-app-install** is marked as a broken package.

---

