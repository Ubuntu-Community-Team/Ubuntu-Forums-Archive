---
title: "Any way to backup what Adept has downloaded?"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by xoros on 2006-06-20
Being on dialup,  I want to know is there some way to save files that Adept downloaded already?  

And if so, if I re-install kubuntu how would I use those files then?

Thanks.

---

### Post by bollix47 on 2006-06-20
Take a look in:

/var/cache/apt/archives

The deb files that you installed should be there unless you deleted them.

Edit:  not sure if adept works the same way but may be storing debs elsewhere??

---

### Post by aysiu on 2006-06-20
Adept is just a frontend for *dpkg*, so the files should be in /var/cache/apt/archives

---

### Post by xoros on 2006-06-20
Thank you both !

---

