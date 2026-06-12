---
title: "Multimedia Codecs"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by yatishmisra29 on 2007-07-17
Hi I have been using ubuntu for past few weeks n have been quite impressed by its features....but problem is that i have no net access...so is there a way by which i can download all multimedia codecs for playing mp3 n other files??
all the solutions given in forum or ubuntu guide says about using apt-get....but i cannot use that because of no net access..

---

### Post by Al3xK3aton on 2007-07-17
Have you tried Earthlink?

---

### Post by jediborger on 2007-07-17
If you have access to another computer that has internet (obviously since you've posted to this forum) even if its a windows computer you can download the debian packages from packages.ubuntu.com. Here's the links for the two packages you want, goto the bottom of the page and download the file for your computer's architecture (usually i386)
[http://packages.ubuntu.com/feisty/libs/gstreamer0.10-plugins-ugly]("http://packages.ubuntu.com/feisty/libs/gstreamer0.10-plugins-ugly")
[http://packages.ubuntu.com/feisty/libs/gstreamer0.10-plugins-ugly-multiverse]("http://packages.ubuntu.com/feisty/libs/gstreamer0.10-plugins-ugly-multiverse")

You can install these packages by typing:
```
sudo dpkg -i <*package name*>
```

These two packages should give you the codecs you want, post back if they don't work or if your computer complains about missing dependencies.

---

### Post by yatishmisra29 on 2007-07-17
thanx...will try it..

---

### Post by bodhi.zazen on 2007-07-17
Also check out AptOnCD : [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

