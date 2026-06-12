---
title: "Restore my USB drive"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by AlienX on 2007-02-23
Hi guys !
I installed USB Knoppix in my USB drive ( Kingston ) . The problem is , I want to use it again as a USB drive . I tried to erase everything there was on it , and then i made a vfat filesystem . Now , when I insert it in a USB slot , it gets mounted automatically , but I can't write to it ( create a new file ) . I even tried remounting it with rw , but it still doesn't work . Any help would be appreciated :)

---

### Post by chggr on 2007-02-23
I think that the USB device doesn't have any problem. The way you mount it is wrong. Try using the option "umask = 000".

To see the available mount options, open a terminal and type in: man mount. Then go to the "Mount options for fat" chapter.

---

