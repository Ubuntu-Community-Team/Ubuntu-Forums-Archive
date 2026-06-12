---
title: "Input/output error"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by crackity on 2005-10-08
I can't log in ubuntu, I get this "session didnt last long enough" 10seconds error.

error:
```

etc/gdm/presession/Default: registering your session with wtmp and utmp
etc/gdm/presession/Default:Running: /usr/bin/x11/sessreg -a -w /var/log/ wtmp -u /var/run/utmp
-x "/var/lib/gdm/: 0.xservers" -h "" -l ":0" "crackity"
-x -session-manager: error while loading shared libraries: mibgpg- error.so.0: cannot open shared object file: Input/output error

```

Thanks in advance

---

### Post by mlomker on 2005-10-09
I can't find any references to that specific error.  The full error log is /var/log/Xorg.0.log.  You can use **nano** to view it if you wish.

I'd try recreating your xorg.conf file:

```

sudo dpkg-reconfigure xserver-xorg

```

---

