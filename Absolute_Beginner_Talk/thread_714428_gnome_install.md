---
title: "gnome install"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by nickburns on 2008-03-03
I have a clean install, off of the alternative CD, command line only system.

I want to add gnome to my install, but not the ubuntu-desktop package.

So basically I want gdm and gnome without all the extra stuff that ubuntu-desktop installs.

What do I need to install?  

What order? configuration?

---

### Post by Joeb454 on 2008-03-03
Well i just did a check, and one of the options available for aptitude is in fact - gnome.

So you might want to look into that. Other than that, I'm not 100% sure :)

---

### Post by Hospadar on 2008-03-03
i think if you install "gdm" it will get you set up with a basic GUI install with a nice graphical login.

```
sudo apt-get install gdm
```

you could also get xfce or kde this way by installing "xdm" or "kdm" respectively (maybe xfce is named a little different, not sure)

---

