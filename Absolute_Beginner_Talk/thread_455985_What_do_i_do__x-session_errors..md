---
title: "What do i do ? x-session errors."
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by ubdai on 2007-05-27
Unable to login.
Getting the following error report.
[COLOR="Red"]
/etc/gdm/Presession/Default: Registering your seesion with wtmp and utmp
/etc/gdm/Presession/Default: running:  /usr/X11R6/bin/seesreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "username"
/etc/gdm/Xsession: Beginning session setup...
x-session-manager:  error while loading shared libraries: libgnomefs-2.so.0:cannot open shared object file: No such file or directory[/COLOR]

Tried several other threads in the forum but they don't seem to fix my problem.

I'm guessing it something in Gnome or to do with login??

All answers appreciated.

ubdai

---

### Post by arijarot on 2007-05-27
I'm not sure, but maybe you can try restarting your gnome display manager ```
gdm-restart

```

---

### Post by ubdai on 2007-05-27
nope, didn't work.

Anyone else got any ideas

ubdai

---

### Post by taurus on 2007-05-27
What steps have you tried so far to resolve that problem?  It would be helpful to know that so others won't suggest the same things that you have already tried.

---

