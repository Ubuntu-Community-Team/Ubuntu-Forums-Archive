---
title: "Deleting Konqueror"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by LaDeDa on 2007-11-14
I just got the KDE CD, but I prefer FireFox as my browser.  Can Konqueror be deleted or should I just leave well enough alone ??    TIA for your help.

---

### Post by Inxsible on 2007-11-14
> **LaDeDa said:**
> I just got the KDE CD, but I prefer FireFox as my browser.  Can Konqueror be deleted or should I just leave well enough alone ??    TIA for your help.

You can remove Konqueror, if you like. But I think it is the default browser for KDE and if you try to remove it, it will also remove kubuntu-desktop. Atleast that's what happens when you try to remove a default app in Ubuntu.

But, kubuntu-desktop is a meta package and you can safely remove it. Only catch is, if and when you try to upgrade your OS from Gutsy to Hardy Heron lets say, you will need to re-install kubuntu-desktop. If, however, you plan to do a fresh install later (like me), then you do not have to worry about it at all

---

### Post by Inxsible on 2007-11-14
Oh and you can remove konqueror by ```
sudo apt-get remove konqueror
```

---

### Post by The Joe on 2007-11-14
You might be able to get away with it now Gutsy uses Dolphin (I think). When I recently did aptitude install kubuntu-desktop it was Dolphin anyway.

---

### Post by Inxsible on 2007-11-14
> **The Joe said:**
> You might be able to get away with it now Gutsy uses Dolphin (I think). When I recently did aptitude install kubuntu-desktop it was Dolphin anyway.
Well Dolphin is the new default File browser, but the web-browser is still Konqueror, I think. Previously, Konqueror was the file browser as well as the web browser.

---

### Post by skyjacker on 2007-11-14
> **Inxsible said:**
> Well Dolphin is the new default File browser, but the web-browser is still Konqueror, I think. Previously, Konqueror was the file browser as well as the web browser.
Unless you are really cramped for space, just leave konkueor on, and add firefox. They will behave with each other.

---

