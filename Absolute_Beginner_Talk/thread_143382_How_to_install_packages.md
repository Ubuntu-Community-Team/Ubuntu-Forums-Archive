---
title: "How to install packages?"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by dearanna on 2006-03-12
Hey all, I need help.

Okay, I downloaded some packages into my windows XP, then burned them to disc. I then booted into Ubuntu and tried to load them with synaptic, but when I tried to add the CD into the repositories, it kept saying, "This is not an Ubuntu CD."

I was just wondering how you load the .deb packages into ubuntu. I loaded the packages into my home directory already, I just don't know how to install them.

Please help.

---

### Post by Klaidas on 2006-03-12
Go to terminal, then enter ```
sudo apt-get install package
```. It will download package from Internet with all the dependencies and install it.

---

### Post by bluevoodoo1 on 2006-03-12
[QUOTE=dearanna]I was just wondering how you load the .deb packages into ubuntu. I loaded the packages into my home directory already, I just don't know how to install them.[/QUOTE]

You're asking, how to install a .deb file? Right? If not, just ignore me... but it's...

```
sudo dpkg -i packagename.deb
```

---

