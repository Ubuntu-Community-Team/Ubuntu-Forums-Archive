---
title: "Installing a new Loding Screen"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Dylnuge on 2007-06-04
Hello,

I am finally starting to change some themes on my Ubuntu system. When I login, I have a new GDM screen, and a background to match. What I don't know how to change is the screen that shows when Loading ubuntu. I know how to do this under KDE, but I am using GNOME, which I have not used much before.

Thanks,
Dylan

---

### Post by shearn89 on 2007-06-04
you can change the little box that pops up saying things like "loading gnome... loading metacity" by putting your custom image in /usr/share/pixmaps/splash. Example code (for terminal):

```
cd yourimagedirectory
sudo mv yourimage.ext /usr/share/pixmaps/splash/ubuntu-smooth.png



```
you may want to backup the original ubuntu-smooth.png

---

