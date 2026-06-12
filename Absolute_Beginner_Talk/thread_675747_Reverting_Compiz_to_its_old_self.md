---
title: "Reverting Compiz to its old self"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by pteri498 on 2008-01-23
I've played around with some of the more popular Emerald themes out there, and I've found some glitchy resizing bars to be too much for me.

Namely, there's no resize anchor for the bottom end of any of my windows.

Whatever the case, there's no default theme for Emerald in the list, and it won't populate when I click to download the GPL and non-GPL themes.

Anybody know how to reset compiz / emerald to its installation state?

Thanks a lot.

---

### Post by chewearn on 2008-01-23
To remove emerald:
```
sudo aptitude remove emerald
```


To delete emerald themes:
Delete the sub-directories under:
/home/<user>/.emerald/themes

To delete current emerald theme:
Delete the files under:
/home/<user>/.emerald/theme

---

