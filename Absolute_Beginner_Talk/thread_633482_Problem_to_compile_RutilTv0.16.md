---
title: "Problem to compile RutilTv0.16"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Fanatico on 2007-12-06
I have Ubuntu 7.10 and I am trying to compile utility RutilTv0.16 and receive the following errors:

$:~/Installations/RutilTv0.16$ ./configure.sh --launcher=external
Using helper_launcher.sh as launcher proxy, you may need or want to tune this script.
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Please install (or upgrade to) GTK+ 2.6.0, at least.

I understand that I have to install gtk+-2.0.pc package

I downloaded libgtk2.0-dev_2.8.20-0ubuntu1.1_i386.deb
When I tried to install it Package Installer says: "Dependency is not satisfiabe: libgtk2.0-0"

I downloaded libgtk2.0-0_2.8.20-0ubuntu1.1_i386.deb
When I tried to install it Package Installer says: "A later version is already installed"

What is wrong? Please help! Thanks

---

### Post by taurus on 2007-12-06
Is your machine connected to the net?  Why don't you just install libgtk2.0-dev with either synaptic or from a terminal.

```
sudo apt-get update
sudo apt-get install libgtk2.0-dev
```

---

### Post by Fanatico on 2007-12-06
Thank you very much! It works!!!

---

