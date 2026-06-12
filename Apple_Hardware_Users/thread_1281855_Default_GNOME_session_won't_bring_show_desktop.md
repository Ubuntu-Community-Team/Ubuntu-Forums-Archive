---
title: "Default GNOME session won't bring show desktop"
date: 2009-10-03
forum: Apple Hardware Users
---

### Post by mattppcintel on 2009-10-03
I recently upgraded to 9.04 and now when I try to log in using the default gnome session I get a black screen with the mouse and nothing else.  If I log in using gnome failsafe everything comes up fine.  Is there a way to reset the default gnome session?  I don't like having to log in to failsafe mode.

---

### Post by stephana on 2009-10-04
Hi,

you can reset gnome by deleting the ~/.gnome folder, but this will also kill many app settings. 

```
sudo rm -r ~/.gnome
```

---

