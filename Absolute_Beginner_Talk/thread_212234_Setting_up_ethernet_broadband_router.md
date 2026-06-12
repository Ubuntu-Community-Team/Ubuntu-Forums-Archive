---
title: "Setting up ethernet broadband router"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by diarmuid on 2006-07-09
Hiya,
Yesterday I installed the 64bit version of linux, and as soon as I started it up, my router, which had already been programed, and was  plugged in via my ethernet port, worked absolutley fine, without me touching a thing.

However, due to some compatability issues, I have reverted to a 32bit version of linux and now, I am unable to get my router working.  My router is a "2wire 1800" and has been preprogramed, the only information I have been able to get from their site is that it should work but they dont offer any support.

Linux recognizes that the connection is active, but firefox, wont connect and the software updates wont download.

Does anyone know why it works on 64 bit and not 32 and how to fix it?

Thanks in advance

Diarmuid

---

### Post by Apple 101 on 2006-07-09
Try deactivating your network card eth0 and reactivating it again.

Gnome: System --> Admin --> Network Manager.
In a terminal: gksudo network-admin

---

