---
title: "ipod - umount vs 'eject'?"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by Seine on 2006-11-25
Hi there

When I *umount /media/ipod* the device cleanly unmounts, but the ipod itself still says "Do not disconnect".

When I select "Eject" from nautilus the ipod says "OK to disconnect".

What's the essential difference? is there a terminal command that can trigger the same effect from the device as the eject command does?

:mrgreen: 

Thanks
seine

---

### Post by jpeddicord on 2006-11-25
I believe unmount does not disconnect the device, it only disables access to it. Eject, on the other hand, unmounts it and disconnects it. I'm not sure if there is a single command to the effect of Nautilus's Eject function.

---

### Post by engla on 2006-11-25
try the command "eject". Seriously. I can't try myself, I don't have an ipod.

---

### Post by Seine on 2006-11-25
You sir are a genius!

*eject ipod* did the trick (where ipod = the path of device after /media/)

Cheers
Seine

---

### Post by LexAevum on 2006-11-29
Um. so what do I do if I umounted /media/ipod and now want to eject it?
D'oh!:-k

---

