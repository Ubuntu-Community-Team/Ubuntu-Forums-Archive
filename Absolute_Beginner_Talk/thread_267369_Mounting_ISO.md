---
title: "Mounting ISO"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2006-09-28
Ok I have a question. I f I have a DVD movie iso, can I mount it and watch it as if it were a disk in my drive?

Thanks.

---

### Post by Jussi Kukkonen on 2006-09-28
```
mount -o loop file.iso /mnt/point

```
That should work. You might have to give the filesystem type too with -t (see *man mount*)

---

### Post by PPAAUULL on 2006-09-28
Thanks for the help!

---

