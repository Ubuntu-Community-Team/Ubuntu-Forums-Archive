---
title: "nvidia-kernel missing - where to get?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by smith.norton on 2007-03-21
I am trying to install nvidia-glx. I have already installed the following two packages.

1. nvidia-kernel-common_20051028+1_all.deb
2. nvidia-kernel-source_1.0.8776+2.6.15.12-28.1_amd64.deb

After installing the above two, I try to install nvidia-glx.

```
smith@everest:~/software/amd64deb$ sudo dpkg -i nvidia-glx_1.0.8776+2.6.15.12-28.1_amd64.deb
(Reading database ... 86526 files and directories currently installed.)
Preparing to replace nvidia-glx 1.0.8776+2.6.15.12-28.1 (using nvidia-glx_1.0.8776+2.6.15.12-28.1_amd64.deb) ...
Unpacking replacement nvidia-glx ...
dpkg: dependency problems prevent configuration of nvidia-glx:
 nvidia-glx depends on nvidia-kernel-1.0.8776; however:
  Package nvidia-kernel-1.0.8776 is not installed.
dpkg: error processing nvidia-glx (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nvidia-glx
```


The error message says that, I must should first install, nvidia-kernel-1.0.8776. But I believe I have already installed the nvidia-kernel-common and nvidia-kernel-source packages. What else do I need to install so that I can proceed with the installation of nvidia-glx?

---

### Post by Bachstelze on 2007-03-21
First, I'm going to assume you have no internet connection on this machine.

nvidia-kernel is a virtual package. It means that it is not a real package you can download as a DEB file but something that is supllied by more than one real package. It contains the nvidia kernel module so there cannot be just one package for it, since there are several different kernels and each of them requires a module built specifically for it. Those modules are non-free so they're not shipped with the default Ubuntu installation, they're in the "restricted-modules" packages.

Long story short : *sudo apt-get install linux-restricted-modules-$(uname -r)*

---

