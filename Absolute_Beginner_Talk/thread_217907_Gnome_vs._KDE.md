---
title: "Gnome vs. KDE"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by lennyjames on 2006-07-17
Hello everyone,
No, this post is not a fist-match between Gnome and KDE! I just wanted to know is a 'package' or a 'program' is 'designed for KDE', does that mean it will not work in Gnome environment? I can see a lot of packages in the Synaptic and I am very curious. 

I am still figuring out the ropes for Linux. Thanks!

---

### Post by Jagot on 2006-07-17
A KDE package will work in GNOME and vice-versa, but it will need to download some extra files to enable it to do so.  Occasionally there are also slight differences in appearance between a program of the native desktop environment and that of another.

---

### Post by lennyjames on 2006-07-17
> **Jagot said:**
> A KDE package will work in GNOME and vice-versa, but it will need to download some extra files to enable it to do so.  Occasionally there are also slight differences in appearance between a program of the native desktop environment and that of another.

Will Synaptic automatically get the files that are required for this to work?

---

### Post by Jagot on 2006-07-17
> **lennyjames said:**
> Will Synaptic automatically get the files that are required for this to work?

Yes

---

### Post by bruenig on 2006-07-17
If you are going to get a non native app it is probably best that you use aptitude from the command line like this
```
sudo aptitude install filename
```
replacing filename obviously. By doing this, when you want to uninstall it, you can use
```
sudo aptitude remove filename
```
and get rid of the massive amount of extra files and dependencies needed, helps keep the disk clean.

---

### Post by aysiu on 2006-07-17
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

