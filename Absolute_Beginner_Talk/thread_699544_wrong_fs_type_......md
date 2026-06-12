---
title: "wrong fs type ....."
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by the beak on 2008-02-17
Hi

 i'm trying to mount my cdrom to /cdrom using the following:

mount -t iso9960 /dev/cdrom /cdrom

and i get the error :

"wrong fs type, bad option, bad superblock on /dev/cdrom, or too many mounted file systems"

i've had previous help to remove autos and user to owner on /etc/fstab but this didn't work.

Can anyone please help?

---

### Post by sb12 on 2008-02-17
> **the beak said:**
> Hi

 i'm trying to mount my cdrom to /cdrom using the following:

mount -t iso9960 /dev/cdrom /cdrom

and i get the error :

"wrong fs type, bad option, bad superblock on /dev/cdrom, or too many mounted file systems"

i've had previous help to remove autos and user to owner on /etc/fstab but this didn't work.

Can anyone please help?

try just mount /dev/cdrom /cdrom

---

### Post by the beak on 2008-02-17
Thqts great thanks. How do u close a thread though. I'm a bit simple

---

### Post by sb12 on 2008-02-17
at the top there should be a part marked thread options and you select mark as solved, something along those lines

---

