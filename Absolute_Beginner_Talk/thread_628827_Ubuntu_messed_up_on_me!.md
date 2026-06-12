---
title: "Ubuntu messed up on me!"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Rileymd on 2007-12-01
I tried to install that Mac package to make Linux look like Leopard and after doing basicially everything I didn't like it and switched my themes and everything back to normal and rebooted, now my close,minimize and maximize buttons are gone and I cannot move my windows at all...Can someone help me please!

---

### Post by jken146 on 2007-12-01
Try ```
metacity --replace
```

---

### Post by Rileymd on 2007-12-01
Ok that worked but whenever I try to enable compiz the same thing happens..Any other suggestions? I was thinking maybe uninstall compiz and emerald and then reinstall them but I'm not sure how do go about doing that

---

### Post by red_Marvin on 2007-12-01
Try removing the emerald and beryl settings, press ctrl+h in nautilus to show hidden files and see if you can find and remove any .beryl .emerald folders, they might be inside other folders in your home directory.

Note, do not delete them permamtly until you know it works.

---

