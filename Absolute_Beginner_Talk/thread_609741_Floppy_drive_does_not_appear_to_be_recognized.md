---
title: "Floppy drive does not appear to be recognized"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by supersk on 2007-11-11
When I go to Places -> Computer -> Floppy and then right-click on Floppy and select Mount Volume nothing happens.

When I double-click on Floppy, it just says opening floppy but nothing else afterwards.

In /etc/fstab there is the following line:

*/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0*

so it looks like it's supposed to be automounting it.  Anyone have any suggestions?

---

### Post by gheorghe_pop on 2007-11-11
It may be that your floppy is broked!

---

### Post by supersk on 2007-11-11
you are right.  just tried this floppy on another computer and it wasn't being recognized either.

i replaced the floppy and all is well.  thanks.

---

