---
title: "download files from terminal"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2007-01-10
My X is not working, and I need to reinstall a driver to get it up again.  How can I use the terminal (and only the terminal) to retrieve a package from an http site?

---

### Post by moeFinley on 2007-01-10
[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool]("http://en.wikipedia.org/wiki/Advanced_Packaging_Tool")

I'm sure if your more specific someone can give you the exact command.

---

### Post by meng on 2007-01-10
aptitude or apt-get is easiest, it will download and install packages for you.
If you have a particular package in mind, you can use wget to download it, but you'll then have to install it yourself.
wget [http://(full](http://(full) path)

---

### Post by oscar78 on 2007-01-10
well i'm trying to download envy from

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I just recently installed a driver for my graphics card, but upon rebooting I get the following error message:

API mismatch: the NVIDIA kernel module has the version 1.0-8776, but this X module has the version 1.0-9746. Please make sure that the kernel module and all NVIDIA driver components have the same version.
Failed to initialize the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly. Please consult the NVIDIA README for details.
***Aborting***
Screen(s) found, but none have a usable configuration.

X will not boot up...

---

### Post by meng on 2007-01-10
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.5-0ubuntu1_all.deb
sudo dpkg -i envy_0.7.5-0ubuntu1_all.deb
```

---

### Post by oscar78 on 2007-01-10
thanks guys!

that was able to install the package I needed, and, more importantly, solved my X problem!

---

### Post by meng on 2007-01-10
Congratulations. Please post back with more questions when problems arise.

---

