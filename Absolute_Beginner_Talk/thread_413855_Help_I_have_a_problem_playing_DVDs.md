---
title: "Help I have a problem playing DVDs"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by beatman on 2007-04-19
Hi there Re the instruction
sudo apt-get install libdvdread3 libdvdcss2 ogle-mmx ogle-gui

I receive the following information:
Reading package lists... Done
Building dependency tree
Reading state information... Done
libdvdread3 is already the newest version.
libdvdread3 set to manual installed.
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

Can anyone help me get my DVDs to run... they worked fin in the earlier version, with Automatix.

Many thanks in advancehttp://ubuntuforums.org/images/smilies/new_popcornsmiley.gif

---

### Post by scanez on 2007-04-19
libdvdcss2 isn't included in the repositories due to legal reasons. Instead, install libdvdread3 first and then check /usr/share/doc/libdvdread3/README.Debian for information on installing libdvdcss2.

---

### Post by Seisen on 2007-04-19
Follow this guide and see if it helps.

[http://ubuntuforums.org/showthread.php?t=413624]("http://ubuntuforums.org/showthread.php?t=413624")

---

