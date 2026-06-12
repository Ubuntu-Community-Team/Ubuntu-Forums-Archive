---
title: "How to uninstall programs"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-02-22
I was just wondering how to un-install a generic piece of software not necessarily supported by Canonical. I would greatly appreciate any help. 

:KS

---

### Post by GameManK on 2007-02-22
Anything you installed from the repositories can be removed the same way.  Just click on remove in synaptic or "apt-get remove" from the command line.

---

### Post by 3rdalbum on 2007-02-22
This all depends.

Did the piece of software come packaged as a .deb? Did it come packaged as a .rpm, with you converting it to a .deb?

If so, you can find it in Synaptic and remove it like you would anything in the repositories.

If you built it from source code, using Checkinstall (i.e. instead of typing "sudo make install" you typed "sudo checkinstall"), you can use Synaptic. It will be listed in the "Checkinstall" category.

I've not tried removing something that I compiled without Checkinstall, so I'll pass that question onto someone else.

---

### Post by tonyr1988 on 2007-02-23
If you install something from source without checkinstall, you must have the original source to uninstall it (which is why most people will recommend checkinstall). But hopefully you didn't have to build something from source in the first place.

---

