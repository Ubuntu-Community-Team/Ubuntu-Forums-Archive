---
title: "iso master"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by patchido on 2008-03-31
is it posible to rip .iso from dvds with this program??? or which one is good?

---

### Post by joshrobinson on 2008-03-31
you can do it multiple ways, you can use gnomebaker, k3b, or the command line

```
sudo umount /dev/cdrom
dd if=/dev/cdrom of=filename.iso bs=1024 
```

you have to change where it says cdrom, to where your cd/dvd drive is located

---

### Post by lbotha on 2008-04-16
I have heard of acetoneISO as well, don't know whether its just for mounting ISO's though..

---

### Post by bulletxt on 2008-04-17
one of AcetoneISO2 features:

- Generate an ISO from a Folder or CD/DVD


[http://www.acetoneiso.netsons.org/viewpage.php?page_id=1](http://www.acetoneiso.netsons.org/viewpage.php?page_id=1)

---

