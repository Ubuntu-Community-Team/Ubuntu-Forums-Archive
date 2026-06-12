---
title: "Kde"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by blendmaster on 2006-10-09
Hello!

Will doing the 

```

sudo apt-get update
sudo apt-get install kubuntu desktop

```

(if that's right, please correct me if I'm wrong) allow me to add the Kubuntu desktop environment to GRUB. 
Also, if this is done, will it just create an entirely new partition for kubuntu, or will it simply add the desktop (which is what I want). 
Lastly, while using it, will I be able to access all of my files saved through Ubuntu.

Thank you!

---

### Post by Jagot on 2006-10-09
You will want:

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)

It will not add KDE to GRUB, but will allow you to select which DE you want at login.  It will not create a new partition, just add the DE.  Yes, you will be able to access all the files.

---

### Post by taurus on 2006-10-09
First off, it's "sudo apt-get install kubuntu-desktop", not "sudo apt-get install kubuntu desktop"!!!  However, I recommand you use aptitude instead of apt-get because it works better with the dependency stuff...

```

sudo aptitude update
sudo aptitude install kubuntu-desktop

```
It will install KDE on your system, NOT on GRUB!  KDE is a window environment and it has nothing to do with GRUB or LILO.  After you install it, you can switch between Gnome or KDE from the Options (bottom left corner) at the login screen.

---

### Post by blendmaster on 2006-10-09
Alright, that cleared up a lot of questions for me. I didn't want a whole new partition, because that would take up a lot of space. Thank you both for replying!

---

