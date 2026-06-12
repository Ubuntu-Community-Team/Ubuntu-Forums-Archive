---
title: "Strange Screen Res Problem"
date: 2005-09-21
forum: Absolute Beginner Talk
---

### Post by DoeRayMe on 2005-09-21
I have edited the xorg.conf file so i can have 1024-768, that works fine.

However i seem to have a black strip down the left side about an inch wide and i cant get rid of it, anyone know how to fix it

i have a Samsung SyncMaster 152v 15" Moniter

Thanks

---

### Post by numberexhaust on 2005-09-21
[QUOTE=DoeRayMe]I have edited the xorg.conf file so i can have 1024-768, that works fine.

However i seem to have a black strip down the left side about an inch wide and i cant get rid of it, anyone know how to fix it

i have a Samsung SyncMaster 152v 15" Moniter

Thanks[/QUOTE]
 try doing the

sudo dpkg-reconfigure xserver-xorg

command, and go to advanced, just accept the values they give you
that worked for me, but my problem was slightly different.

---

### Post by mlomker on 2005-09-21
> i have a Samsung SyncMaster 152v 15" Moniter


You'll need to go into your monitor's menus and adjust the width/height/centering, etc.  Hopefully you have a manual for your monitor...

---

### Post by DoeRayMe on 2005-09-21
[QUOTE=numberexhaust]try doing the

sudo dpkg-reconfigure xserver-xorg

command, and go to advanced, just accept the values they give you
that worked for me, but my problem was slightly different.[/QUOTE]
 Nope, that didnt work, thanks anyway

---

### Post by DoeRayMe on 2005-09-21
[QUOTE=mlomker]You'll need to go into your monitor's menus and adjust the width/height/centering, etc.  Hopefully you have a manual for your monitor...[/QUOTE]
 How do i do that?

---

### Post by tseliot on 2005-09-21
[QUOTE=DoeRayMe]How do i do that?[/QUOTE]
I think he means the (physical) buttons on your Monitor (not in Ubuntu).

---

### Post by DoeRayMe on 2005-09-21
[QUOTE=tseliot]I think he means the (physical) buttons on your Monitor (not in Ubuntu).[/QUOTE]
 Fixed, thanks

---

