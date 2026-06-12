---
title: "[SOLVED] Winefix uninstall problem."
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by TidusBlade on 2007-10-23
Well I installed winefix recently and it seems to bring up problems, I can install programs but cannot uninstall them, so I tried uninstalling winefix using Synaptic, which didn't do anything.
Anyways then I tried with the terminal and got this;
```
watermelon@blayde:~$ sudo dpkg -r winefix
(Reading database ... 139475 files and directories currently installed.)
Removing winefix ...
update-mime-database: I don't have write permission on /usr/local/share/mime.
Try rerunning me as root.

Aborted (core dumped)
dpkg: error processing winefix (--remove):
 subprocess pre-removal script returned error exit status 134
+ [ ! -f /etc/gnome/defaults.list.bak ]
+ [ -f /etc/gnome/defaults.list ]
+ cp /etc/gnome/defaults.list /etc/gnome/defaults.list.bak
+ grep -o -m 1 winefix /etc/gnome/defaults.list
+ match=
+ [  != winefix ]
+ echo application/x-ms-dos-executable=winefix.desktop
application/x-extension-lnk=winefix.desktop
application/x-extension-msi=winefix.desktop
+ tee -a /etc/gnome/defaults.list
application/x-ms-dos-executable=winefix.desktop
application/x-extension-lnk=winefix.desktop
application/x-extension-msi=winefix.desktop
+ gtk-update-icon-cache /usr/share/icons/gnome
+ update-mime-database /usr/share/mime/
+ update-mime-database /usr/local/share/mime
update-mime-database: I don't have write permission on /usr/local/share/mime.
Try rerunning me as root.

Aborted (core dumped)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 134
Errors were encountered while processing:
 winefix
watermelon@blayde:~$ 

```
I cant open some programs either, so I decided to leave it and ask for help, since I dont want to screw it up more than how it is already. So if anyone can help me here I'd really appreciate it :grin:

---

### Post by Vadi on 2007-10-23
This was an issue with winefix on Fiesty, but it was already fixed - so you must've installed an old version of it.

Click here ([click]("http://ubuntuforums.org/showpost.php?p=3502345&postcount=26")), I posted a solution.

---

### Post by TidusBlade on 2007-10-23
Thanx :) Forgot to mention I'm using Feisty.

---

### Post by Vadi on 2007-10-23
Yeah. The dev fixed that problem, so if you install his latest .deb, it'll work okay :)

---

