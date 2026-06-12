---
title: "xorg.conf Problem"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by BlueK on 2007-11-01
I tried to set up my duel screens so my bigger one was the default (1280x1024) and the smaller one (1024x768 ) was the secondary screen. I went into 'xorg.conf' and was able to do what I wanted, after I restarted, it was fine (Bigger screen was default). But I was missing my window bars on my programs on the secondary screen, so I went back to undo my changes, but after I restarted again, both screens are now mirrors of each other and stuck at 800x600. Is there anyway I can get back to the basic original 'xorg.conf'?

---

### Post by Pumalite on 2007-11-01
Always backup before editing a file.

---

### Post by BlueK on 2007-11-01
Yes, I've had to learn that now the hard way, but can I get it back at all?

---

### Post by PmDematagoda on 2007-11-01
Try:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

