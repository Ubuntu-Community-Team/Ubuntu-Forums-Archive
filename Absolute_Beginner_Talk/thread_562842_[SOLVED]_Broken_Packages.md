---
title: "[SOLVED] Broken Packages"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by axamax on 2007-09-29
I just installed Ubuntu last night and am running as a dual boot with XP (ubuntu is on second hard drive.
I am getting an error saying I've two broken packages:
linux-image-generic
linux-restricted-modules-2.6.20-16-generic

When I try to reinstall them using the Synaptic Package Manager I get the following error.

E: /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.32_i386.deb: subprocess pre-installation script killed by signal (Segmentation fault), core dumped

How do I rectify this. I am brand new to Ubuntu and still trying to find my way around

---

### Post by Happy_Man on 2007-09-29
Wow.... that's a new error. Here, try this. Open a terminal (Applications --> Accessories --> Terminal and type this in: ```
sudo apt-get autoclean
sudo apt-get install linux-image-generic linux-restricted-modules-2.6.20.16-generic
```

---

### Post by axamax on 2007-09-29
Thanks for your help.
Initially it said the modules would not be installed and to use "sudo apt-get install -f" with no modules.
After doing this it worked.
Thanks again.

---

