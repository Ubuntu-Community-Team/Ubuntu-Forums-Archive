---
title: "LOGNAME not found in pbuilder"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Hendrixski on 2007-08-07
I don't recall pbuilder ever doing this before:

```

dpkg-source: warning: no utmp entry available and LOGNAME not defined; using uid of process (1234)

```

It's not finding my LOGNAME, which is set to my login.  Other people have posted and normally they've been told to just use dpkg-buildpackage or debuild.  I use those as well, but pbuilder is invaluable for me when I try to backport things.

I've attached the log of the entire pbuilder script.

---

