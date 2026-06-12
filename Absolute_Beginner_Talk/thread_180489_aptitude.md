---
title: "aptitude"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-05-22
I heard that when I install a metapackage with aptitude it I can easily remove all the packages later, does that mean that if I install gnome with it i could remove it later?

thanks,
josh:D

---

### Post by Klaidas on 2006-05-22
You can allways revome packages that you have installed.

---

### Post by Caligula on 2006-05-22
yeah..
but you need to do it manually, and if you installed ubuntu-desktop as a metapackage it can be a big headache...

---

### Post by aysiu on 2006-05-22
Yes, if you install with aptitude, it will make it easier to uninstall later: ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

If you accidentally install with apt-get, all is not lost, but it is a bigger pain. You can use something called *deborphan* to find the "orphaned" packages after you remove the *ubuntu-desktop* metapackage.

---

### Post by nanotube on 2006-05-22
[QUOTE=Caligula]I heard that when I install a metapackage with aptitude it I can easily remove all the packages later, does that mean that if I install gnome with it i could remove it later?

thanks,
josh:D[/QUOTE]
to make things clear after all the replies - YES, aptitude keeps trackof all the dependencies, so you should be able to easily uninstall gnome afterwards with a simple "sudo aptitude remove ubuntu-desktop", and it will uninstall all the dependencies, not just the metapackage (if you installed with aptitude in the first place, of course).

---

### Post by wthanna on 2006-05-22
If Aptitude does such a good job of resolving and tracking dependencies, etc. How come it is not the default?  Why do people always recommend (in this forum, generally) apt-get install "file" rather than aptitude? Is there a downside to aptitude?

---

### Post by aysiu on 2006-05-22
[QUOTE=wthanna]If Aptitude does such a good job of resolving and tracking dependencies, etc. How come it is not the default?  Why do people always recommend (in this forum, generally) apt-get install "file" rather than aptitude? Is there a downside to aptitude?[/QUOTE] Habit. Also, sometimes, you don't care about tracking all the dependencies and such. Generally it becomes an issue only for metapackages.

---

### Post by Caligula on 2006-05-22
[QUOTE=nanotube]to make things clear after all the replies - YES, aptitude keeps trackof all the dependencies, so you should be able to easily uninstall gnome afterwards with a simple "sudo aptitude remove ubuntu-desktop", and it will uninstall all the dependencies, not just the metapackage (if you installed with aptitude in the first place, of course).[/QUOTE]

Thank you!

---

