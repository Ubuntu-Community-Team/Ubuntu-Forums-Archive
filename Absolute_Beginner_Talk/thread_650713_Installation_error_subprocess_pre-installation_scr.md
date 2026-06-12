---
title: "Installation error: subprocess pre-installation script killed by signal"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by taqkavar on 2007-12-26
Hi, I am switching to Ubuntu, but when I try to install firefox plugins or when updating Ubuntu I get these errors:

The Java(TM) Plug-in, Java SE 6
E: /var/cache/apt/archives/sun-java6-bin_6-03-0ubuntu2_i386.deb: subprocess pre-installation script killed by signal (Segmentation fault), core dumped
E: /var/cache/apt/archives/sun-java6-jre_6-03-0ubuntu2_all.deb: subprocess pre-installation script killed by signal (Segmentation fault), core dumped

Adobe Flash Plug-in
E: flashplugin-nonfree: subprocess post-installation script killed by signal (Segmentation fault), core dumped

When trying to update
E: /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb: subprocess pre-installation script killed by signal (Segmentation fault), core dumped


Can someone please help me with this? I have no idea what to do now :( It will be really appreciated.

---

### Post by Maxtorm on 2007-12-30
Perhaps your apt cache is corrupted? From a Terminal window, try this:
```
sudo rm /var/cache/apt/*.bin
sudo apt-get update
```
Then attempt to install the plugins again.

---

