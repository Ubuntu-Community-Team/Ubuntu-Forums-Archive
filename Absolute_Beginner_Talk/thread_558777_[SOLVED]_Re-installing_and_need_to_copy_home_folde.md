---
title: "[SOLVED] Re-installing and need to copy home folder to cdrw - need full access from l"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-09-24
Some files have an X marked on them so I cant copy them onto my cdrw. Really need to do this before reinstall.

I'm using cd/dvd creator from places on the live cd.

---

### Post by master_kernel on 2007-09-24
> **philinux said:**
> Some files have an X marked on them so I cant copy them onto my cdrw. Really need to do this before reinstall.

I'm using cd/dvd creator from places on the live cd.
Try this on the folders with an x:
```
sudo chmod -R 777 FOLDER
```

---

### Post by philinux on 2007-09-24
Ok I could do that for my home folder but whats the effect of this when I reinstall and copy it back on to my hard drive. Wont all the permissions need resetting?

---

### Post by philinux on 2007-09-24
Anyone?

---

### Post by Henry Rayker on 2007-09-24
What kind of items in your home folder would not be permissible for you to write? Couldn't you just open the cd/dvd creator using gksudo? I believe you should be able to do a gksudo nautilus and find it through there, but I'm not certain. I haven't ever tried this before and I'm not at my own machine right now...

---

### Post by philinux on 2007-09-24
I'm booting from the live cd cos system buggered

---

### Post by philinux on 2007-09-25
Feel a fool gksu nautilus but forgot where to look. like in media ):P
You learn something everyday. Thank god for the live cd.

---

