---
title: "acroread crash"
date: 2005-09-04
forum: Bug Reports / Support
---

### Post by lizhao on 2005-09-04
My acoread always crash after the splash screen popups.
My config:
Ubuntu 5.10
acroread 7.0-0.9 or  7.0-0.9~5.04ubp2

how to solve it? ](*,) 

thanks in advance

---

### Post by Manny C on 2005-09-04
Use xpdf. Plus Install libttf2 and t1lib1 packages.

Acrobat is fat and slow. Plus its closed source. I only use it for pdf's that are scanned copies of journals.

---

### Post by ulisse on 2005-09-05
Try also Evince, it's way better than xpdf!

---

### Post by Victorious on 2005-09-20
Acrobat Reader 7 requires libstdc++5 (some name like that) library, just install this package (note that libstdc++ 6 will not solved the problem (installed by default)).
Acrobat Reader is faster than other pdf reader when open large files, expecially files with image, it's also support file detach, easily bookmark, etc...It's closed source but it's free!

---

### Post by RyanGT on 2005-12-08
Thanks for this.  The libstdc++5 solved the problem for me as well.

---

