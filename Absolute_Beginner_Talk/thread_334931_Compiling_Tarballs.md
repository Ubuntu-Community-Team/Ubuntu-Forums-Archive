---
title: "Compiling Tarballs"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Riyonuk on 2007-01-09
I usually try to find my programs through the synaptic package manager. But of course, they dont have every program known to mankind u_u, so I'm asking how to compile this tar.gz or tar.bz2?

I know I need to install a package called "build-essential", and it seems doing the "make install" command never works for me. Anyone care to make a quick noob guide, or point me in the right direction?

---

### Post by 23meg on 2007-01-09
Check these out:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Riyonuk on 2007-01-09
Well if build-essential is just a "pointer that tells Synaptic/Adept/aptitude to install a bunch of other real packages", are these included on the 6.10 disc? I go to the cd, navigate to /pool/b/ and go to build-essential, and theres a .deb, installing this will install it and its dependencies, or am I going to have to search for those too?

---

### Post by taurus on 2007-01-09
Insert the CD into the drive and at the prompt, type

Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by Riyonuk on 2007-01-09
Thank you :D

Edit: Both of you guys/girls

---

