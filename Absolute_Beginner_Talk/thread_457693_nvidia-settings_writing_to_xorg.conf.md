---
title: "nvidia-settings writing to xorg.conf"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by grejm on 2007-05-28
I have installed the nVidia drivers, and they work, but when I try to press the button "Save to X configuration file", it says "Unable to create new X backup file '/etc/X11/xorg.conf.backup'

What to do?

---

### Post by aldreis on 2007-05-28
Try this:

```
gksudo nvidia-settings
```

It should work. ;-)

---

### Post by grejm on 2007-05-28
....and it did. Thanks a bunch!

---

