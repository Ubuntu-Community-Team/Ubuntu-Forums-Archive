---
title: "Help: Can't log in anymore"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by nwr222 on 2007-02-11
I have a problem logging in.
The error seems to be creating some file on start up.

I get the following error in a warning panel
Your session only lasted less than 10 seconds......
in the details i can see
-----------------
/etc/gdm/Presession/Default: Registering your session with wtmp and utmp
/etc/gdm/Presession/Default: running /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l "0" "linux"
/etc/gdm/Xsession:Beginning session setup...
mkdtemp: private socket dir: No space left on device
-----------------
In my playing with Xubuntu, one of the things that I have done is to switch on backup, which I think is going to /var/backup.  Could this have filled the partition?

In any case, all I can get now is a tiny command line window.  Problem is I don't know what to do next.

---

### Post by nwr222 on 2007-02-11
Played around and managed to get into a root window and delete the backup files.
Sure enough I can now log in.  I have changed the backup destination to a partition with much more space.  This is one that is actually a NTFS windows partition but it seems to be backing up OK.

Time to reallocate some space I think
:)

---

