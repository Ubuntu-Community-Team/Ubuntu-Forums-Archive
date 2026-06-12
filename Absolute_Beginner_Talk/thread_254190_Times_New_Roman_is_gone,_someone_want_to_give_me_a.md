---
title: "Times New Roman is gone, someone want to give me a copy?"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Silver Streak on 2006-09-09
In the process of removing some non-default fonts, I accidentally trashed Ubuntu's "Times New Roman" font. Con someone help me out and get me the font? It sould be located somewhere in /usr/share/fonts/truetype/

Thanks!

SS

---

### Post by powder on 2006-09-09
Just reinstall msttcorefonts.

```
sudo aptitude remove msttcorefonts
sudo aptitude install msttcorefonts
sudo fc-cache
```

---

### Post by croak77 on 2006-09-09
Too slow

---

