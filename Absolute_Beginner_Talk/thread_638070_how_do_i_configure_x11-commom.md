---
title: "how do i configure x11-commom"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by determinedblkman1 on 2007-12-11
trying to put  a GUI on my ubuntu server 7.04 i installed the x11-common package w/o a hitch, but now i dont see the config file so i dont know how to get it up and running? 

  any help please

---

### Post by taurus on 2007-12-11
Why not just install the ubuntu-desktop package?

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by Dr Small on 2007-12-11
Most people who run servers, only want a simple Window manager that won't hog resources.

Install Xorg
```
sudo apt-get install xorg
```

And then install whatever window manager/desktop environment you want.

---

