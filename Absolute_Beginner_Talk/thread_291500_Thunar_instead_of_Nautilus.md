---
title: "Thunar instead of Nautilus?"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-11-02
Hi.

I really want to use Xfce's Thunar file manager instead of Nautilus.

What should I do so that my folders open with Thunar? And I mean all folders, even when I click on them in the Places menu.

Cheers.

---

### Post by picpak on 2006-11-02
Try:

```
sudo dpkg-divert --divert /usr/bin/nautilus.ubuntu --rename /usr/bin/nautilus
sudo ln -s /usr/bin/thunar /usr/bin/nautilus
```

---

### Post by TheMono on 2006-11-02
WARNING: If you do this, it will (I believe) screw up your desktop, which is drawn by Nautilus. Further, strange things will happen. Trust me, I tried it and ended up going back.

---

### Post by zugu on 2006-11-03
Isn't there a simpler, safer way to select the default application to open directories? It should be as simple as it is to change the default opener for text or multimedia files - right-click, properties, open-with.

---

