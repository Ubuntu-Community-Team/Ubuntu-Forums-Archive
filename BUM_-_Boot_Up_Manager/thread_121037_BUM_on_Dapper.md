---
title: "BUM on Dapper"
date: 2006-01-24
forum: BUM - Boot Up Manager
---

### Post by hda on 2006-01-24
Hi,
can't get BUM 2.1.4-1 to run.

Error message:
```
Can't locate object method "signal_connect_after" via package "Gtk2::CheckButton" at /usr/lib/perl5/Gtk2/GladeXML.pm line 40.
```

Any suggestions?

---

### Post by zAo on 2006-01-27
Same here, wanna know too.

---

### Post by ZeBob on 2006-01-28
+1
I've got a problem with another perl-gtk2 software, i wonder if perl is the origin of thoses problems.

---

### Post by hda on 2006-01-28
Problem vanished after libglib update

---

### Post by saltydog on 2006-01-31
Yes, it was a libglib bug.

---

