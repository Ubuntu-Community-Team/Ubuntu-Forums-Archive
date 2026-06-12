---
title: "Failed to configure USB: could not set config 1: Operation not permitted"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by c0d4041292 on 2008-04-08
Failed to configure USB: could not set config 1: Operation not permitted

how to fix this?
how do i permit my app to be able to config this

---

### Post by red_Marvin on 2008-04-08
In what context do you get this error? What program gave it and what were you trying to do?
I would guess that it is a permission problem though, are you running something that should be run as superuser as a normal user?

---

### Post by c0d4041292 on 2008-04-08
i am using QLandkarte, and i get the error when i try to download stuff from the gps device
add: how would i run as a superuser

---

### Post by red_Marvin on 2008-04-09
Try pressing Alt+F2 and when the dialog comes up type *gksudo qlandkarte* and press enter.
The dialog is like windows' run dialog, and gksudo is used to run stuff as superuser.
I've had problems myself to communicate with usb devices as andything else than superuser.

---

