---
title: "headphones make sound not work"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Trianth on 2007-05-19
After plugging in my headphones, I realized that they weren't working.  So I unplugged them, naturally, and now the sound won't come out of the speakers without a reboot.  Any fix to this?

---

### Post by Pragmatist on 2007-05-19
Check the volume settings before and after plugging in the headphones.  In a terminal:
```
alsamixer
```

Or, if your in GNOME, just Right-click the volume applet at the top right of your screen (or type CTRL + O).  Make sure you go to the Edit-->Preferences menu and select all the necessary volume controls.  Also, check File-->Change Device  and make sure the right device is selected.

Let us know how these experiments go.

---

