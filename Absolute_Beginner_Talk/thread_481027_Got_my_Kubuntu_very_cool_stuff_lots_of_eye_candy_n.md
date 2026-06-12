---
title: "Got my Kubuntu very cool stuff lots of eye candy now how do I get rid of gnome?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2007-06-22
I tried "sudo apt-get remove gnome-desktop" No luck. Any ideas? Let me know please.

---

### Post by NeoLithium on 2007-06-22
```
 sudo aptitude remove ubuntu-desktop
```

---

### Post by raul_ on 2007-06-22
sudo aptitude remove ubuntu-desktop

read the list carefully, because it's very likely that it will drag a lot of programs with it. Take note of the ones you use, and then install them later (no gedit for example)

---

### Post by NeoLithium on 2007-06-22
Generally KDE has a lot of applications that are installed with Kubuntu-desktop which are equally compatible, such as gedit turns to kate or kwrite, stuff like that.  It all depends on if the user is really really attached to some gnome apps or not ;)

---

### Post by swoll1980 on 2007-06-22
thanks guys!!

---

### Post by swoll1980 on 2007-06-22
I've only had ubuntu for 3 weeks so I'm not attached to anything yet I tried the pclinux live CD right before I got ubuntu I liked ubutu way better, but I did like the kde desktop I'm so happy I can have both.

---

### Post by swoll1980 on 2007-06-22
nolan@BIGMAN:~$ sudo aptitude remove ubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
nolan@BIGMAN:~$ 

nothing happend? Any ideas?

---

### Post by raul_ on 2007-06-22
probably you deleted a package that was part of the metapackage before...

you should 

sudo aptitude install ubuntu-desktop

so that is installs the missing programs  and then try to remove it again

---

### Post by swoll1980 on 2007-06-22
thanks I'll try it

---

