---
title: "[SOLVED] external hdd?"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2008-03-02
I have an external hdd, but only windows can see it. Does anyone know why that would be? Is there some software that I need?

---

### Post by Crooksey on 2008-03-02
Is it NTFS? If the log on the hard disk is corrupted, then you may need to mount with..

```

$ mount -f /dev/sda1 /mnt/usbdisk
```

---

