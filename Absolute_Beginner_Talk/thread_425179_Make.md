---
title: "Make"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by ziffnabb on 2007-04-27
Hi:
I am trying to install avant window navigator.  I ran ./configure ok, but when trying to run make, I got 

make: *** No targets specified and no makefile found.  Stop.

I see files called makefile.am and makefile.in, but no make.

The output of configure included this:

No package 'gtk+-2.0' found
No package 'gdk-2.0' found
No package 'libwnck-1.0' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


What should I do?

Thanks,
Ziffnabb

---

### Post by Cypher on 2007-04-27
Because of those errors, no Makefile was created. You have to get "./configure" to succeed before anything good will come.

Make sure you have those particular packages installed by
```

dpkg -l | grep <PKG>

```
where <PKG> is "gtk+", "gdk", "libwnck" and "gconf"

---

### Post by aysiu on 2007-04-27
Try this:
[HOW-TO: Compile Avant Window Navigator](http://ubuntuforums.org/showthread.php?p=2093300)

---

