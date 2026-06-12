---
title: "Fonts,Fullscreen,Wine"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Xalan on 2007-03-14
Been digging through the forums and have been fiddling around with winecfg, anyways my question is i've got a game i'm running that the text flashes and disappears also it doesn't seem to want to run in full screen though that is probably a setting i haven't figured out yet with wine, as far as the flashing goes though someone on another thread suggesting grabbing the fonts from a windows box and putting them in the wine folder but i can't actually seem to find the wine folder if anybody has any suggestions to these problems please drop me a line thankee

---

### Post by Jonam on 2007-03-15
Wine folder should be under your home directory - it appears as .wine if you do a directory list:

```
desktop:~$ ls .* | grep -i wine
.wine:

```

. To change to it, type:
```

cd .wine
```

Jonam

---

