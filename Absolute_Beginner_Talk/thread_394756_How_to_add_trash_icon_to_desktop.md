---
title: "How to add trash icon to desktop?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by FeraTech on 2007-03-27
Ok, I've been using Ubuntu for over 1 year and I feel really dumb asking this since it is probably very easy.

How can I add the trash icon to my desktop? Having it on the bar means I accidentally open up my trash way too often. I want it away from my bars so I don't accidentally keep clicking it.

---

### Post by lamalex on 2007-03-27
remove it from panel (if you want)
and then in terminal do the following
```

ln -s .Trash/ Desktop/Trash

```
then if you want change the icon.

---

### Post by compmodder26 on 2007-03-27
As far as I know, that won't update the icon when the trash is full or empty.  To get the icon to change by itself you should open gconf-editor (in terminal, type "gconf-editor") and click apps->nautilus->desktop.  Then check "trash_icon_visible".

---

