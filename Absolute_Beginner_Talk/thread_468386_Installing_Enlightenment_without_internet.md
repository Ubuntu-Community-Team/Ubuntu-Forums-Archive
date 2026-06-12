---
title: "Installing Enlightenment without internet?"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by shamushand on 2007-06-08
I need help, how can I install Enlightenment (16 or 17) without internet on Ubuntu 7.04? Will it work if I just download and install all .deb packages and restart the system? Please help!

---

### Post by 5-HT on 2007-06-08
> **shamushand said:**
> Will it work if I just download and install all .deb packages and restart the system? Please help!

Yup :) No need to restart the system, just X to boot into E from gdm/kdm/xdm...etc

---

### Post by shamushand on 2007-06-08
Are you really sure? I've heard you have to compile some sort of script or something. Don't I have to make enlightenment my default desktop environment? I'm afraid  might hose the system again...

---

### Post by 5-HT on 2007-06-08
Are you trying to install E16 or 17? If you install the offical ubuntu debs (E16 only), an option to boot into Englightenment will be automagically added to GDM/KDM. If you really want, you can always make a custom .xinitrc/.xsession. E17 will require a little bit more fooling around, but there is a great walkthrough on the forums for how to get it setup with Ubuntu.

---

### Post by shamushand on 2007-06-08
Either one, but since you said that E16 is the official, I'll go with that. 

Last time I tried installing the .deb packages, I couldn't because of "Error: Dependency is not satisfiable: Libc6". :(

---

### Post by shamushand on 2007-06-08
One last thing - how many packages are there? Because I come up with about 30 packages, is this correct?

---

### Post by 5-HT on 2007-06-08
> **shamushand said:**
> One last thing - how many packages are there? Because I come up with about 30 packages, is this correct?

Take a look at packages.ubuntu.com. The only ones you absolutely need are the dependencies. You may already have a few of those installed.

---

### Post by shamushand on 2007-06-08
Thank you very much, you've been very helpful to me! :p

---

