---
title: "Nvidia GPU not supported"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by ChiaroScuro on 2006-12-02
I have tried to install the beta drivers from Nvidia. I was successful in the installation w/ the x86 installer. I then proceeded with:

sudo apt-get install linux-headers-$(uname -r) build-essential
sudo /etc/init.d/?dm stop
sudo sh NVIDIA-Linux-x86-1.0-*-pkg1.run

It didn't go through!
said something like GPU not supported, then exclaims that I could view the installer log.

I Ran /var/log/nvidia-installer.log to see the results and it wouldn't let me.

What is wrong here?

---

### Post by pay on 2006-12-02
run ```
nano /var/log/nvidia-installer.log
```

---

