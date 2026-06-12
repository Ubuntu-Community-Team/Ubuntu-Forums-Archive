---
title: "Help with bonfire installation"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by Captaingracekidd on 2006-06-12
Tried to install bonfire.... this is what it said at startup.

23329: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 243.
This is normally a bug in some application using the D-BUS library.

** (bonfire:23329): WARNING **: Hal connection problem :  No property storage.cdrom.write_speed on device with id /org/freedesktop/Hal/devices/storage_model_SONY_CD_RW_CRX140E

It opened the window but the warning scared me so what's up with this?

---

### Post by taurus on 2006-06-12
Warning is not the same as error message.  There is nothing to be scared of.  It just tells you that it is having a problem with storage.cdrom.write_speed but the program should still function...

---

