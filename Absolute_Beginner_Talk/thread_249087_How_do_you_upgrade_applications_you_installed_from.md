---
title: "How do you upgrade applications you installed from source?"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-09-02
For applications complied and installed from source, how do you go about upgrading (or even 'uninstalling' the older version)those applications, when newer versions are available?

Thanks!

---

### Post by kidders on 2006-09-02
Hi there,

Tricky one :P

If you've done from-source installations, you'll no doubt be familiar with typing stuff like

```

./configure && make && make install

```

What you may *not* know is that the "install" in "make install" is called a target. Whoever wrote the thing you're compiling will have defined a target called "install" that does some useful things for you. Typing "make" on its own usually executes the default target, which is often a compile operation.

Anyhow, what you need to figure out is whether your app's Makefile contains any other interesting targets, such as "upgrade", or maybe "uninstall". If these are not present, you're in a spot of trouble!

**FINDING OUT WHAT TARGETS ARE DEFINED**
Every now and then, a clever-clogs writes a "help" target, which often spews out some useful information on other make targets and what they do. Failing that, it's time to get your hands dirty.

Enter your source directory and type ** cat Makefile | less** What you're looking for is lines that start with a single word + a colon. These are target definitions.

**WHAT IF THE MAKEFILE WON'T UNINSTALL?**
First, check for an obviously-named uninstaller script, maybe **uninstall.sh** or something. Failing that, the easiest thing to do is to re-execute the "make install" and copy the output into a text document. Observe each copy ("cp") or similar command, and reverse each one manually.

Tedious, I know, but straightforward.

Any help?

---

### Post by kinematic on 2006-09-02
instead of using make install you should install the checkinstall package from the repository.
instead of installing the software like make install does it creates a .deb package wich you can easily uninstall with apt-get/synaptic like any other app you install with it.

---

### Post by kidders on 2006-09-02
Now that's a MUCH smarter suggestion :) Thanks kinematic!

---

