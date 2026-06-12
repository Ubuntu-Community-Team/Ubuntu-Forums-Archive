---
title: "what's the command to c all your ide devices"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2007-03-31
i keep loosing my ide cd-rom and i want to c if the kernel is still cing it yet

---

### Post by Adramelech on 2007-03-31
what you mean by losing?
Your devices are located under /dev/

---

### Post by lime4x4 on 2007-03-31
it doesn't show up under my computer and if i insert a cd nothing pops up.
lsusb lists devices that are usb. So i was wondering if there was a command like that for ide devices as well

---

### Post by jvc26 on 2007-03-31
```

sudo fdisk -l

```
lists your drives.
Il

---

