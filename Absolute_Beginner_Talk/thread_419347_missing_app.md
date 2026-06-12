---
title: "missing app?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by doubleuicked on 2007-04-22
when i first install ubuntu which was only a few days ago, the desktop effect thing was working fine, now when i try to open it says "the composite extension is not available"

does anyone know why?

cheers,

---

### Post by Ziox on 2007-04-22
did you install the binary driver for your graphics card?
and what is your graphics card?


also, did you recently edit the xorg.conf file?

---

### Post by doubleuicked on 2007-04-22
oooo, um i recently got a driver update thing that prompted me to install a driver for my ati card i believe and the file started with a xorg or something, 

could i somehow reactivate the desktop effects?

---

### Post by Ziox on 2007-04-22
you can try xgl and beryl.

sudo aptitude install beryl xserver-xgl emerald

then start beryl by entering:

beryl-manager

---

### Post by doubleuicked on 2007-04-23
ok perfect 

thanks !!

---

