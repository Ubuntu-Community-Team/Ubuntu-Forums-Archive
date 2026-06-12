---
title: "Default directory in nautilus"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by sunexplodes on 2007-02-18
I was wondering if there was an easy way to make nautilus open in a specific folder by default.

For instance, I have an icon on my panel that opens up Nautilus, but it always opens in my home folder by default. I want it to open in a different one. Is there a method?

Also, is there a way to make specific applications remember what directory i last opened a file in? Every time I open more than one file, i have to navigate to the directory for each file opened.

---

### Post by yabbadabbadont on 2007-02-18
Right-click on the panel icon for nautilus and in the field where it launches it, add the full path to the directory that you want it to open.  I think that will work.

---

### Post by aysiu on 2007-02-18
> **yabbadabbadont said:**
> Right-click on the panel icon for nautilus and in the field where it launches it, add the full path to the directory that you want it to open.  I think that will work.
For example, let's say you want it to always open to /home/sunexplodes/music/ instead of /home/sunexplodes

You would right-click the icon and change the command from ```
nautilus
``` to ```
nautilus ~/music
```

---

### Post by sunexplodes on 2007-02-18
perfect. that worked like a charm. knew it would be something simple. thanks guys!

now, any ideas for my second question?

---

### Post by yabbadabbadont on 2007-02-18
> **sunexplodes said:**
> perfect. that worked like a charm. knew it would be something simple. thanks guys!

now, any ideas for my second question?

Unfortunately (for you :D) that is application specific behavior.  The only way to do it would be to change the settings in each individual application.  (assuming that they even support that option)

---

