---
title: "How to clear partially installed DPKG items"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by taddy_porter on 2007-11-10
I've been playing around with hosting a small local site on my computer. As part of the process I installed drupal through synaptic. It errored out on the database creation.

I've successfully configured it myself and am using drupal now. The problem I have is that dpkg still thinks it wasn't installed correctly so every time I use apt-get it tries to reconfigure the database. I'm trying to install webmin as well and it's erroring out because of the drupal configuration.

How do I remove the drupal settings so it leaves drupal but stops trying to configure it?

I tried dpkg -A drupal-5.1 but it said package not found. I also tried the --clear-all or whatever that command is, but it didn't work either.

---

### Post by louieb on 2007-11-10
or something like
```
sudo dpkg --configure -a
```

or whatever just throw stuff at the wall and see what sticks.:biggrin:

---

### Post by taddy_porter on 2007-11-12
Nope, that doesn't work.

---

