---
title: "startup script for 'checkgmail'.."
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by yeehawjared on 2006-08-25
total noob question:

I have a symlink at \etc\rcS.d\S91jaredscript that links to \etc\init.d\jaredscript  (all permissions are set to a+x)

jaredscript contains the following:
#! /bin/sh
mount /dev/sda5 /media/STORAGE
checkgmail&

the mount command works great, but for some reason checkgmail isn't starting when Gnome loads up.  Am I going about this the right way?  All I want is for the checkgmail application to launch upon startup.

---

### Post by yeehawjared on 2006-08-25
figured out my own question

go to System > Preferences > Sessions
look for the "startup programs" tab and add it there.

---

