---
title: "X server Failed after install"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by michaelof36 on 2006-11-30
Early I was having problems installing Ubuntu 6.10 so I tried the alternate cd. Now I have it installed, but it still says "xserver failed to load....." blah blah blah asks if I want to see the report its the same report as before. I have an ati radeon x800 installed, my motherboard is intel based and I'm dual booting Windows XP and Ubuntu using grub. How can I get xserver properly configured so that I can get the interface running smoothly? Also I can run Ubuntu in rescue mode.

---

### Post by taurus on 2006-11-30
Boot into recovery mode and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

---

