---
title: "[SOLVED] Renaming CD Drive"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-06-06
I am using the -16 kernel and until recently i had a phantom drive icon in nautilus. I rectified that by looking up the alias of my dvdrw dvdrom cdrw and cdrom in /dev. They all pointed to hda

So i changed my etc/fstab and put in hda instead of 'scd' which was previously there in -15 and worked fine.

Anyway, now my cd drive is named 'CD-RW/DVD±RW Drive (2)'

I tried to change the name to 'CD-RW/DVD+_ RW Drive' i.e. tried to remove the (2) from it and it gives me an error
```
Sorry, couldn't rename "CD-RW/DVD±RW Drive (2)" to "CD-RW/DVD±RW Drive".
```

Its trivial, but annoying !

Thanks

---

### Post by Inxsible on 2007-06-06
Bump

---

