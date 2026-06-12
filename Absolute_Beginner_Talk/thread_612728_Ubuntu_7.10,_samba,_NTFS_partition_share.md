---
title: "Ubuntu 7.10, samba, NTFS partition share"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by qreg on 2007-11-14
Well, I've spent the last two days searching for solutions on how to share my NTFS drive using SAMBA on my Ubuntu 7.10 machine. 

So far I managed to make the shared assets visible from my Win XP laptop, however when I attempt to access those files a message like this pops up 

```
\\Wojtek-dektop\hda5 is not available (accessible) You may not have access rights and so on.
```

Those NTFS drives are accessible for me using my Ubutu so they should be properly mounted.

---

### Post by qreg on 2007-11-14
Sorry for bothering everyone, I've managed to get it going. Had to run ntfs-config and enable writing for both internal and external devices, dont know why this had anything to do with readonly shareing but that fixed it.

---

### Post by matt.parkes on 2007-12-04
Great!  Thanks alot!  Worked for me!

---

