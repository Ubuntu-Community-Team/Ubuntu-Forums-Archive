---
title: "theme: icon question"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by sohaibma on 2007-03-09
when i install a theme in edgy, where (in which directory) is the battery (or power) notification item saved?

---

### Post by lamalex on 2007-03-09
should be /usr/share/pixmaps i believe.

---

### Post by jem7v on 2007-03-09
Any custom icon themes you install are saved in subdirectories of ~/.icons and the directories are named after the themes. (~ means /home/username/ for future reference, in case you don't know yet.)

Each of those directories (one for each theme) will usually have several subdirectories into which all the icons are sorted.  You'll have to sort through them to find the icon, because every artist  seems to label them and sort their icons differently.

---

### Post by sohaibma on 2007-03-12
where is the human theme battery icon stored? I looked in the .icons directory and its not there

---

### Post by Najand on 2007-03-12
> **sohaibma said:**
> where is the human theme battery icon stored? I looked in the .icons directory and its not there
An easy fast wat to fiind it is:
```

locate battery

```

---

### Post by jem7v on 2007-03-13
The Human theme one won't be in there because it's a default icon set rather than custom.  Only the extra icons you install yourself end up in ~/.icons

Default icon themes are found in the subdirectories of /usr/share/icons

---

