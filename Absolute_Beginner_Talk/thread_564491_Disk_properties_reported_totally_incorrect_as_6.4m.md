---
title: "Disk properties reported totally incorrect as 6.4meg should be 1.6gig?"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-10-01
When I right click on my 3.8gig pen drive and select properties is displays 41 items totalling 6.4 meg. Free space 2.2 gig

This pen drive has a backup of my home folder on it 3.8 -2.2 = 1.6 gig. Whats going on?
See screenshot attached.

---

### Post by justleen on 2007-10-01
does ```
 df -h 
``` give the same output?
can you go into the folder, and do a du?
```
 cd /media/disk
du -hs 
```

edit:  "Quad Shot of Ubuntu" :  sorry for the code blocks!, only noticed that after reply..

---

### Post by philinux on 2007-10-01
Here is the output of those commands. Thanks for reply.

---

### Post by justleen on 2007-10-01
its reporting the right sizes there...   might be a glitch in the GUI, how its calculating/displaing ?
was it still copying anything in the background perhaps? 

unmounting/ mounting wont work?

I would want to worry about is to much, since DF en DU are both showing the correct sizes..

---

### Post by philinux on 2007-10-01
Well annoying it must be a bug ?

---

### Post by justleen on 2007-10-01
doenst sound like a feature :)

---

