---
title: "Burn-applications malfunctioning"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Captaingracekidd on 2007-01-23
I have tried burning my mp3 library on dvds but when the disc is done it turns up as text-files that can't be opened followed by a crash of KNotify. This has happened with K3B, Gnomebaker and Bonfire.
I read somewhere that starting the app from sudo could correct the problem but this is what it says right before launching.


[I]lucifer@boris:~$ sudo bonfire start
libnotify-Message: Unable to get session bus: No reply within specified time
6434: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 243.
This is normally a bug in some application using the D-BUS library.

** (bonfire:6434): WARNING **: Hal connection problem :  No property storage.cdrom.write_speed on device with id /org/freedesktop/Hal/devices/storage_model_SONY_CD_RW_CRX140E
[/I]

Then the program opens and after that KNotify crashes.

Please help me! ](*,)

---

