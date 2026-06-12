---
title: "Permissions on an OS X Drive"
date: 2006-07-01
forum: Apple PPC Users
---

### Post by JPMaximilian on 2006-07-01
I used to have a powerbook g4 notebook, but recently the logic board went out and I didn't want to fork over $450 to get a new board.  I took the hard drive out and hooked it up to an external firewire enclosure, to my delight, the drive was automatically discovered and mounted by ubuntu on another PC.  I can access all of the system files, but under my personal user folder, I can't access the files because I don't have the permissions.  This is a good thing, if my laptop was stolen, people wouldn't be able to look at my files, but is there a way for me to access my own files, since I know the password?  Any help would be much appreciated.

---

### Post by aysiu on 2006-07-01
Actually, anyone who was savvy enough can easily access your files unless they're encrypted (are they?), so you can just launch a file browser as root and then see any files you want.

Press Alt-F2 and type

**Gnome**: ```
gksudo nautilus
``` **KDE**: ```
kdesu konqueror
``` **XFCE**: ```
gksudo thunar
``` I'm not sure what it is for Edubuntu, though...

---

### Post by JPMaximilian on 2006-07-01
Ah, well, my laptop wasn't secure then, but that's good I suppose since if I had enabled filevault (encryption) I wouldn't be able to access it with Ubuntu?  Thanks for the help, I now have my files back!

---

