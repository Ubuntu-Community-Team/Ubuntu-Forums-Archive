---
title: "Can't delete a shortcut on my desktop"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Steel Frog on 2007-07-17
I made a shortcut on my desktop to an application I was runnig with WINE (WoW) but now I can't delete the icon. I right-click and select "move to trash" but nothing happens.

What's up?

---

### Post by dfreer on 2007-07-17
It probably has some incorrect permissions set. Can you post the output of this command?
```
ls -al ~/Desktop/
```

---

### Post by Steel Frog on 2007-07-17
Here's the shortcut:
```
lrwxrwxrwx  1 steelfrog steelfrog   43 2007-07-03 17:51 nj -> /media/DATA/Games/World of Warcraft/WoW.exe
```

[EDIT] It says I'm not the owner. o0

---

### Post by dfreer on 2007-07-17
Try a:
```
sudo rm -v ~/Desktop/nj
```
If "nj" is indeed the name of the shortcut according to ls -al

---

### Post by Steel Frog on 2007-07-18
> **dfreer said:**
> Try a:
```
sudo rm -v ~/Desktop/nj
```
If "nj" is indeed the name of the shortcut according to ls -al

That did it! Thanks!

---

