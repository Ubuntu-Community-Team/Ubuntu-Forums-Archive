---
title: "Please help!"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by royksol on 2007-04-05
I wanted to uninstall Nvidia driver. I went to Synaptic Package Manager searched for nvidia, marked all installed things and made complete removal. :( 
This way I crashed Xserver. I've made xorg.conf backup, but now Xserver couldn't find not only nvidia driver, but also nv driver.
I really don't know what to do. When I type
> sudo apt-get install nvidia-glx nvidia-kernel-common 
I've got some error (don't remember exactly) Unable to fetch package or something like this.

---

### Post by Zuuswa on 2007-04-05
try using the command
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by heimo on 2007-04-05
Try installing nv driver.
```
sudo aptitude install xserver-xorg-video-nv
```If that doesn't help, could you try to give more details about the error message?

---

### Post by royksol on 2007-04-05
I'm not at home now, but today I'll try it. Thank you.

---

### Post by Roger D on 2007-04-05
The easiest way to install Navidia drivers, and much else besides, is via Automatix:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Roger D

---

### Post by Jussi01 on 2007-04-05
> **Roger D said:**
> The easiest way to install Navidia drivers, and much else besides, is via Automatix:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Roger D

automatix is a script that tries to install some software, and often fails and breaks systems. We don't provide support for it, and we strongly discourage its use. Problems caused by Automatix are often hard to track and solve, and it might sometimes be easier to install a fresh copy of Ubuntu

---

