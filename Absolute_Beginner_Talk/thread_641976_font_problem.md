---
title: "font problem"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by scrimple101 on 2007-12-16
hello, i installed some extra fonts in the /home/robert/.fonts folder and i can see them there. My problem is that i can't use them in Abiword or OoWriter. Does anyone have any ideas about how to get them working in applications. the fonts work fine in Scribus. Regards, Rob.

---

### Post by jordanmthomas on 2007-12-16
Try running this and then restarting abiword / openoffice / whatever

```
sudo fc-cache -f
```
This will regenerate the font cache.
Also, make sure the fonts are just in ~/.fonts and not any subfolders within it (simply because I KNOW it works that way and I'm not sure about subfolders).

---

### Post by scrimple101 on 2007-12-16
Hello, thanks for your suggestions - i tried but still no luck - i wonder why they wont show up?
Regards, Rob

---

### Post by jordanmthomas on 2007-12-16
What format are the fonts? (ttf, .fon, etc)

---

### Post by scrimple101 on 2007-12-16
they're x-font-ttf type font files

---

