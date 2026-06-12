---
title: "Noob Alert:Can I install both KDE and Gnome?"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by Squatpuke on 2006-03-17
.
.
I have ubuntu installed....can someone direct me to a howto?



or give some advice?

---

### Post by meborc on 2006-03-17
yes

**sudo apt-get install kubuntu-desktop**

that is the command to enter in the terminal...

---

### Post by jrib on 2006-03-17
I recommend that you use aptitude:

```
sudo aptitude install kubuntu-desktop
```

It will make removing kubuntu-desktop and all its dependencies that got installed, if you ever decide to do so, a lot easier

---

### Post by Adrian on 2006-03-17
Installing the **kubuntu-desktop** package will do the trick.

However, the KDE programs will show up in your GNOME menus and vice versa. Some people like this, but others want to keep the menus separate. If you're one of them, check out this thread:
[http://www.ubuntuforums.org/showthread.php?t=123969](http://www.ubuntuforums.org/showthread.php?t=123969)

[QUOTE=meborc]
**sudo apt-get install kubuntu-desktop**
[/QUOTE]

However, if you want to be able to uninstall it easily, it is a good idea to use **aptitude** instead of **apt-get**. It remembers each package that is installed (apt-get doesn't).

---

