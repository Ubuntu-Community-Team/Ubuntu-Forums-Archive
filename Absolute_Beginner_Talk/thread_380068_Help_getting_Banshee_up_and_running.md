---
title: "Help getting Banshee up and running"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Roger_Melly on 2007-03-09
I am at this stage:

Building libipoddevice

libipoddevice requires HAL 0.5.2 or later, which requires a fairly new D-Bus, hotplug, and udev. Any system running GNOME 2.11/2.12 should meet these requirements however (SuSE 10, Ubuntu Breezy, Foresight Linux, Fedora Core 4, Gentoo Linux 2006.0). Also required are development packages for glib/gobject.

After obtaining sources from a tarball or SVN, extract/change into the root libipoddevice source directory, and, if from SVN:

$ ./autogen.sh --prefix=/usr

OR, if from tarball:

$ ./configure --prefix=/usr

Then,

$ make && sudo make install

configure should automatically detect if you have pmount enabled. However, you can specify custom unmount/eject commands by passing --with-unmount-command="/path/to/unmount %d and --with-eject-command="/path/to/eject %d. Also, %d can be used for a device node, %m for a mount point, and %h for a HAL Volume ID.

If you are using submount, you can pass --enable-submount to configure if it is not automatically detected. 

Where is the source directory????

---

### Post by ArieT on 2007-03-09
Please use your package manager for installing software. Banshee is in edgy on the universe repos.

---

### Post by joselin on 2007-03-09
```
sudo apt-get install banshee
```

---

### Post by Roger_Melly on 2007-03-09
ArieT,

Thankyou, I like this advice.  I have downloaded Banshee from the add/remove manager but reading the web site I was under the impression that this was an add on for iPods.  Am I wrong????:confused:

My Synaptic only lists an older version of libipod.

---

