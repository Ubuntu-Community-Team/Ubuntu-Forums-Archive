---
title: "Kde"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by Weebs on 2006-03-15
Hi, I was wondering that if ounce you install KDE on Ubuntu, is there a way to revert back to GNOME?

---

### Post by Xian on 2006-03-15
Not as easily as you installed the environment. You basically have to remove the major KDE libs (found among the kubuntu or kde metapkg), and then the rest will generally follow along.

---

### Post by Weebs on 2006-03-15
Ah, because I wanted to see if I liked KDE better or not (Don't really feel like downloading the Live CD)

---

### Post by Peter41az on 2006-03-15
Did you load KDE by using sudo apt-get install kde-desktop?

---

### Post by Adrian on 2006-03-15
If you use aptitude when installing **kubuntu-desktop**
```

sudo aptitude install kubuntu-desktop

```
...you will be able to remove it by doing a...
```

sudo aptitude remove kubuntu-desktop

```

**aptitude** handles meta-packages better than **apt-get**.

---

### Post by Weebs on 2006-03-15
Thanks for the help :) I was really curious on the KDE enviorment :)

---

