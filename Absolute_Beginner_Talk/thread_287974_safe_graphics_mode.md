---
title: "safe graphics mode?"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by TheNemeses on 2006-10-29
ok whenever i boot ubuntu the graphics mess up and get all garbled and it just happened, never happened before, how do i fix this or is there a way to boot in like a "safe graphics mode" or something like that

---

### Post by taurus on 2006-10-29
Boot into recovery mode from GRUB and at the prompt, type

```
dpkg-reconfigure xserver-xorg
```

---

