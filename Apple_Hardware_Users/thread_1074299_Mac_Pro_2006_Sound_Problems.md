---
title: "Mac Pro 2006 Sound Problems"
date: 2009-02-19
forum: Apple Hardware Users
---

### Post by jaisin on 2009-02-19
This is my third time trying to install Ubuntu. I managed to get everything working properly except sound. I searched the forums, but I'm not able to find what to do. I would like to get the internal speaker working at least. The optical out would be nice, but I can live with it if its too hard. Anyone out there have some suggestions?

---

### Post by cyberdork33 on 2009-02-19
> **jaisin said:**
> This is my third time trying to install Ubuntu. I managed to get everything working properly except sound. I searched the forums, but I'm not able to find what to do. I would like to get the internal speaker working at least. The optical out would be nice, but I can live with it if its too hard. Anyone out there have some suggestions?
run
```

alsamixer -c 0
```
and make sure that your channels are turned up and unmuted.

---

### Post by jaisin on 2009-02-21
Tried that, no luck.

---

### Post by cyberdork33 on 2009-02-21
> **jaisin said:**
> Tried that, no luck.
what channels were available?

---

