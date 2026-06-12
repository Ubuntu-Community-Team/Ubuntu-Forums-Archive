---
title: "bare bones install"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by HappyFeet on 2007-07-17
i want to install the server edition with just gnome and no programs installed. is it:```
sudo apt-get install gnome-core
``` or something else?

---

### Post by tarek on 2007-07-18
I think you need xorg and gdm  to login.

Gnome:
```
sudo aptitude install gnome-core xorg gdm
```

KDE:
```
sudo aptitude install kde-core xorg kdm
```

TK

---

### Post by tarek on 2007-07-18
By the way since you're using a server, you might wanna try XFCE (xubuntu) desktop. It's lighter than gnome and kde.

TK

---

### Post by HappyFeet on 2007-07-18
thanks alot, i'll give it a try. tarek, i downloaded the tv remote in your sig. works great. double thanks.

---

### Post by tarek on 2007-07-18
> **HappyFeet said:**
> thanks alot, i'll give it a try. tarek, i downloaded the tv remote in your sig. works great. double thanks.

Thanks! :)

tarek

---

### Post by aysiu on 2007-07-18
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by RedSquirrel on 2007-07-18
If you wanted to try Xfce without having to install Xubuntu (and all its programs) there is the xfce4 metapackage in the repositories which will install only the basic dependencies for Xfce.

Here's another link regarding barebones installations:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

