---
title: "Need to install a desktop environment, where do I begin"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Zoroaster on 2007-08-20
I installed Ubuntu on a VM but now I want to install GNOME or KDE, first what do you all recommend for the graphical environment, and secondly how do I go about installing it?

---

### Post by w4ett on 2007-08-20
From the terminal type:

```
sudo apt-get install gnome-desktop
```

This should install Gnome and all required packages.

---

### Post by mysticmatrix on 2007-08-20
We don't really RECOMMEND a DE. All I can tell you is how you can install them.

Just install and check them all out and see what you like best.
Here's a guide to install KDE,XFCE, and more.

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by Ferri on 2007-08-20
It's difficult to get everyone to recommend the same desktop. However, Ubuntu is primarily a GNOME distribution, and would get the majority of the votes here.
This should do the work:
```
sudo apt-get install gnome-desktop
```

---

### Post by Zoroaster on 2007-08-20
Thanks

---

### Post by Hobo Joe on 2007-08-20
Use 'aptitude' instead of 'apt-get', it has less of a chance of causing problems.

---

### Post by Ek0nomik on 2007-08-20
> **Hobo Joe said:**
> Use 'aptitude' instead of 'apt-get', it has less of a chance of causing problems.

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

Also, I'd like to point out that searching for gnome-desktop yields no results...

---

### Post by Zoroaster on 2007-08-20
Well , used sudo apt-get install gnome and it's downloading now.  If it is problematic I will use aptitude.

---

### Post by Sye d'Burns on 2007-08-20
```
sudo aptitude install ubuntu-desktop
```

---

### Post by Zoroaster on 2007-08-20
I am getting a gtk-Warning: cannot open display

I assume my display is not setup, any pointers?

---

### Post by w4ett on 2007-08-20
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Initially select 'vesa' as the driver, then select your required resolutions...save, and then:

```
startx
```

---

