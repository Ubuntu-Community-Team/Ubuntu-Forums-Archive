---
title: "More problems in ubuntu"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by MONODA on 2007-11-22
hi everyone i am kind of new to linux and ubuntu and love it! but i keep on getting some weird problems for example when ever i log out, i dont hear the logout sound that i used to hear in feisty. Also, sometime when I logout, it does not do it properly so when i log in i just get the brown wallpaper that is shown when u start logging in and nothing else. any help woild be greatly appreciated.

---

### Post by por100pre1 on 2007-11-22
Check in Sound Properties:

```
gnome-sound-properties
```

If that is not enough try setting the sounds using GDM setup:

```
gksu /usr/sbin/gdmsetup
```

---

