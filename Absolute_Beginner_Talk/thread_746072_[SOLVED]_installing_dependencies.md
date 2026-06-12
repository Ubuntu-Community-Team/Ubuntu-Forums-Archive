---
title: "[SOLVED] installing dependencies"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by StOoZ on 2008-04-05
this is just a theoretical question, for educational purposes only:
I have a program, which I have to install from source , and in its requirement, it says that the following dependencies are required:
> #  GTK+ >= 2.10
# libglade >= 2.3
# libmcs >= 0.4.0
# libmowgli >= 0.3.0 (0.4.0 for Mercurial) 

Now , lets assume that I dont have them, how do I install each one of them?

---

### Post by Paqman on 2008-04-05
If they're available through Synaptic, that's the way to go. In fact, that's the general rule for software in general.

If you do have to compile stuff from source, using checkinstall is a good idea. It'll turn your source code into a standard .deb package so that you'll be able to uninstall it through Synaptic.

---

### Post by kellemes on 2008-04-05
> **StOoZ said:**
> this is just a theoretical question, for educational purposes only:
I have a program, which I have to install from source , and in its requirement, it says that the following dependencies are required:


Now , lets assume that I dont have them, how do I install each one of them?

You can start looking in the online [Package List]("http://packages.ubuntu.com/") for those packages you need.
And (assuming you have the needed repositories enabled) simply install them like so..
```
sudo apt-get install packageX
```

---

### Post by fatality_uk on 2008-04-05
And of course if you download the debs from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for a specific package you need, you can store them offline and combine them into an archieve and script an install so that

---

### Post by StOoZ on 2008-04-05
thank you all! :KS

---

