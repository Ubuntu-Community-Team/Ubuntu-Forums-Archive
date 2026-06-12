---
title: "mutter-3.3 with gnome-shell-3.2 rebuilding possible?"
date: 2012-01-13
forum: Any Other OS
---

### Post by deepclutch on 2012-01-13
Since I am facing [issues]("http://www.debianuserforums.org/viewtopic.php?f=7&t=1577") with nvidia driver and  libmutter0 and gnome-shell, I was thinking of rebuilding  mutter-3.3(libmutter0 to be precise) with gnome-shell-3.2. before that, I  want to know if this is even possible? I have the mutter-3.3 debianized  source avialable from a ppa meant for ubuntu. ([https://launchpad.net/~ricotz/+archive/testing]("https://launchpad.net/%7Ericotz/+archive/testing"))

Is  there a lot of mismatch(error) bound to occur? I was thinking of  editing debian/control to fix the versions  of gtk libs as build deps to  the 3.2.x versions available in Debian. 

Is this possible?

edit:  now I noticed, that libmutter0 is a dependency for gir1.2-mutter-3.0,  gnome-session and gnome-shell. I want to ask, if it is even possible to  rebuild Gnome3.3 Shell,Session and mutter-3.3 in Debian Gnome-3.2  system. the issue is , the development libraries available in Debian will be especially like libgtk-3 are all 3.2.x only. will that compile if I edit control files to correct versions.

TIA+

---

