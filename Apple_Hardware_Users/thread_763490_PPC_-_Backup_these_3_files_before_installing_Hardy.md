---
title: "PPC - Backup these 3 files before installing Hardy"
date: 2008-04-23
forum: Apple Hardware Users
---

### Post by stream303 on 2008-04-23
With Hardy release about a day away, I thought I'd point out three important files to backup or print out to aid in troubleshooting should problems occur.

Aside from backing up your normal data, I'd definitely back these up:

```
/etc/yaboot.conf

/etc/X11/xorg.conf

/etc/fstab
```

The idea here isn't to provide a direct replacement from backup, but to provide a way to manually restore certain elements that might be useful from the older configuration files.

Newcomers to Hardy may be surprised to see how bare their xorg.conf file is, and perhaps certain elements from the old configs could be edited back in if it comes to that.

Previously, my yaboot.conf needed no special append parameters, but this time, I need "nosplash" if I want to see something other than a totally black screen until gdm login.

Things are a little bit different, but if problems occur having that data from the older working configs might save some headaches.

Also note that screen resolution problems may or may not be fixed by the usual "dpkg-reconfigure xserver-xorg" routines - in fact, it may leave your xorg.conf unworkable, killing your mouse, etc requiring manual editing.

I guess we'll have to see, but if you can get to a terminal even in the wrong resolution, it looks like we may have to rely on xrandr to get in the ballpark with something like this (on my 20" G5):

```
xrandr -s 1680x1050 -r 60
```

and then possibly following up with

```
gksudo displayconfig-gtk
```

Hopefully everything will go well, and there's no way to predict until actual release if any of this will be necessary.

---

