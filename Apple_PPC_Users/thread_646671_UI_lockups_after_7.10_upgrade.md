---
title: "UI lockups after 7.10 upgrade"
date: 2007-12-21
forum: Apple PPC Users
---

### Post by svref on 2007-12-21
I've got a g3 ibook that's worked well for years but immediately after upgrading to 7.10 from 7.4 it started to lock up 20-300 seconds after logging into gnome.  There's about a 50% chance of this lockup per boot.

The mouse cursor still moves.

The keyboard and mouse buttons are dead.

C-Alt-f1 to escape to virtual terminal doesn't work.

The only thing I can think to do is reboot.

If the machine lasts 5 minutes w/o lockup, it lasts forever.

(I'm also experiencing another problem, possibly related, that "gnome settings daemon" fails to start.  I dismiss the dialog box but don't know what it means...)

Are these lockups endemic to others, or am I just lucky?  What could be the problem?

---

### Post by Gen2ly on 2007-12-22
The best thing you can probably do at this time is to see if the configurations have become somewhat corrupt.  Usually this is not much of a problem in linux but it does happen.  rename .gconf .gconfd .gnome and .gnome2 and try to reboot.  If this doesn't solve the problem it like has to do with xorg.conf.  Look at the Xorg.0.log and try to track and error warnings.

---

