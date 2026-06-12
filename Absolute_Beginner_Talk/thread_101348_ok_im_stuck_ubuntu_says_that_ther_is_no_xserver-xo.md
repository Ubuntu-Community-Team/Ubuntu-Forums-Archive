---
title: "ok im stuck ubuntu says that ther is no xserver-xorg installed"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by reddog on 2005-12-09
i have the disk here i dont know how to install xserver-xorg i gather so that will work with my video stuff plese help me

---

### Post by aysiu on 2005-12-09
Do you already have Ubuntu installed?

What did you do to prompt it to say it doesn't have xserver-xorg installed? Did you type a command? Click on something?

What does your screen look like right now?

When you first popped the installer CD in, did you just hit Enter or did you type in *server* or *expert* by accident?

---

### Post by Gustav on 2005-12-09
install ubuntu-desktop by typing
```
sudo apt-get install ubuntu-desktop
```
It seems as you did a server or expert install that didn't install the standard packages for ubuntu. They are all depending on the ubuntu-desktop metapackage so by installing that all necessary packages will be installed.

---

