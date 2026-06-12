---
title: "Red and blue reversed on old Powerbook G4"
date: 2006-10-26
forum: Apple PPC Users
---

### Post by earth2mark on 2006-10-26
Just installed Edgy on an old Powerbook G4.  Everything is great, except the colors are seemingly reversed.  Instead of an orange background, everything is blue.  Wherever there should be orange in a normal Ubuntu install, its blue.

Seems like some kind of display or graphics card driver issue.  Has anyone seen this?

Thanks!

---

### Post by anders_gud on 2006-10-27
AIGLX on unpatched xorg has an endian bug (welcome to the world of linuxppc), see:
[http://ubuntuforums.org/showthread.php?t=281762](http://ubuntuforums.org/showthread.php?t=281762)
for a solution...

---

