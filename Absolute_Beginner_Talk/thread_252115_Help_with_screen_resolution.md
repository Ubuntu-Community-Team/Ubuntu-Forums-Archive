---
title: "Help with screen resolution"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by smokeysaysno on 2006-09-06
I shut down my computer last night after an update.  When I turned it back on this morning my resolution was 640x400.  I tried to change the settings but that is the only option.  How can i change it back to my regular setting?

---

### Post by bruce89 on 2006-09-06
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Control+Alternate+Backspace.

---

### Post by smokeysaysno on 2006-09-06
Thanks so much.  It worked perfectly!

---

