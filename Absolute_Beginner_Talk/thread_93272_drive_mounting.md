---
title: "drive mounting"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by grim918 on 2005-11-21
how do i mount an external drive to my linux system. can anyone help me out

---

### Post by Brunellus on 2005-11-21
is it a USB drive?  if your'e running plain old ubuntu it should mount automatically.

---

### Post by dubz on 2005-11-21
[QUOTE=Brunellus]is it a USB drive?  if your'e running plain old ubuntu it should mount automatically.[/QUOTE]

as he said, but you can do this aswell

mount -t <filesystem> /dev/sda1 <mount_point>
if its usb

---

