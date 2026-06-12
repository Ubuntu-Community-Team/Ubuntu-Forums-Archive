---
title: "Can I name an ext3 partition?"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by caughran on 2008-01-09
I've got a large usb external drive mounted. I discovered that it didn't consistently mount the partitions in the same order, so their names were different from one run to the next.

I used ntfslabel to put names on the ntfs partitions; they are now mounted as ntfsback1 and ntfsback2. This is progress; previously they were disk or disk-n.

There's an ext3 partition which is mounted as disk. For consistency, I'd like to give it a name to mount by. Is this possible?

---

### Post by yabbadabbadont on 2008-01-09
```
sudo tune2fs -L MyNewExt3Label /dev/????
```
:D

---

### Post by caughran on 2008-01-09
Thanks! it now mounts as ububack, and I can refer to it in a script.

---

