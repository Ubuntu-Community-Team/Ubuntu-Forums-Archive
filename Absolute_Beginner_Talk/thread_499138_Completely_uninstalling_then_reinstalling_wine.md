---
title: "Completely uninstalling then reinstalling wine"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by Hork on 2007-07-12
sudo apt-get remove wine doesn't completely uninstall wine.  Are there any other functions I can use to completely uninstall it then reinstall it?

---

### Post by felicity on 2007-07-12
```

sudo apt-get --purge remove wine

```

---

### Post by pinoyskull on 2007-07-12
this thread might help you :)
[http://ubuntuforums.org/showthread.php?t=245474](http://ubuntuforums.org/showthread.php?t=245474)

---

### Post by Hork on 2007-07-12
I tried the suggestions in this thread and that thread, but whenever I try

sudo apt-get install wine

It dosn't download a new package. :(

[edit] Ha!  It seems sudo apt-get clean worked.

Thanks for the help!

[edit2]  Gah, still getting an error.

Is it possible to reset winecfg?

---

### Post by zvacet on 2007-07-12
Home folder>view>show hidden files and you will see **.wine folder**.Delete it and after that try to install wine again.

---

