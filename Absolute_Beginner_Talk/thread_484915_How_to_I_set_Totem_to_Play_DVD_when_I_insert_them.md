---
title: "How to I set Totem to Play DVD when I insert them?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by zazen666 on 2007-06-26
Now, when I insert a dvd in to my computer, gxine attempts to open the dvd. 
However, some of these dvd's dont play with gxine, but play fine with totem, so I would like to set totem to be my defult player.

How do I do this with xubuntu?
Thanks

---

### Post by Chris S. on 2007-06-26
I don't know if this is different with Xubuntu, but in plain, ole' Ubuntu you go to System -> Preferences -> Removable Drives and Media -> Multimedia Tab.  I looked it up for Xubuntu and maybe it's Applications -> Settings -> Settings Manager, then File Manager -> Advanced Tab -> Configure the management of removable drives and media.  I hope that's right.

Either way, there should be a Video DVD command line that you can change to run totem when a DVD is inserted.  Totem ran by default for me, but I changed it.  I think the original command was "totem %s", but you could try instead "totem /dev/cdrom" and change cdrom to whatever your DVD device is in the /dev directory.  I run VLC instead of totem, because it works better with DVD menus and chapters.

---

### Post by redcharlie on 2007-07-08
You need gnome-volume-manager (the daemon) and gnome-volume-properties (the gui), which work fine with xfce but don't seem to be installed by default.

Go to system->add/remove and then search for "removable" and the Removable Drives and Media app should appear.  Install it.

The icon should then appear under Settings->Removable Drives and Media
If it's not there, edit /usr/share/applications/gnome-volume-properties.desktop so that the line
OnlyShowIn=GNOME;
is commented out or deleted.

---

