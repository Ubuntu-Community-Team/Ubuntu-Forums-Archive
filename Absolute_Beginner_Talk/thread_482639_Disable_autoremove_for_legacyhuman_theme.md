---
title: "Disable autoremove for legacyhuman_theme?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Thav on 2007-06-23
Hi. So since upgrading to Feisty, it's always bugging me to autoremove the legacyhuman_theme every time I use apt-get. Thing is I like and *use* legacyhuman, so I don't want to remove it. On the other hand there are a handful of packages I would like to be able to use autoremove for.

Is there a way to disable some autoremove flag on legacyhuman-theme, or is there maybe a newer replacement that isn't obsolete in apt-get's eyes?

---

### Post by yabbadabbadont on 2007-06-23
```
sudo apt-mark unmarkauto legacyhuman-theme
```
That should do it.

---

### Post by Thav on 2007-06-23
Perfect, thank you!

---

