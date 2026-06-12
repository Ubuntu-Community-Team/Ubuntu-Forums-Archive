---
title: "dzen2"
date: 2008-05-07
forum: Arch and derivatives
---

### Post by Barrucadu on 2008-05-07
Is anyone here using dzen2? I have been trying to find a good script to display battery info, memory usage, cpu usage and network up/down. I have found a few scripts that only do *one* of those things, but I can't seem to combine them into a working script...

---

### Post by ynnhoj on 2008-05-08
the easiest way to do this would be to use nicely formatted conky output.  [there's a build of conky in the aur that doesn't have any x11 dependencies](http://aur.archlinux.org/packages.php?ID=11884), so you can use that and pipe the output into dzen2.  and [this thread on the arch forums](http://bbs.archlinux.org/viewtopic.php?id=40637) will give you many good ideas!  check out other people's configs.

---

### Post by Barrucadu on 2008-05-08
Right, I've got it all set up how I want it. However, the dzen bar appears above everything else. Is there some way of 'telling' Xmonad to not to use the top X pixels of the screen? If not, how else could I stop it covering things I need to see.

---

### Post by ynnhoj on 2008-05-09
yip, you can set a *defaultGaps* variable in your configs.  [the xmonad page in the archwiki](http://wiki.archlinux.org/index.php/Xmonad#Making_room_for_conky_or_tray_apps) has more details.

edit: oh, upon closer inspection, that setting might disappear soon!  are you running 0.7, or the latest (darcs) version from the aur?  if so, you may need to look into *avoidStruts* or something like that.

---

