---
title: "Help"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by elangley on 2007-04-24
i downloaded the nvidia-glx.deb package on my mac and burned it to a cd, but when i click on the package in ubuntu is gives me this error: Depenency is not satisfiable: nvidia-kernel-1.0.8776

---

### Post by mac.ryan on 2007-04-24
The error is self explenatory, I suppose. In order to help more info are needed, like:
[LIST]
[*]why you can't use the repo version of the package
[*]video card model
[*]version of ubuntu
[*]kernel version [type "uname -r" if you don't know it][/LIST]

---

### Post by elangley on 2007-04-24
nVidia Geforce FX 5800
don't know what repo version means
the kernel is 2.6.20-15-generic

---

### Post by elangley on 2007-04-24
i'm on feisty fawn

---

### Post by mac.ryan on 2007-04-24
> **elangley said:**
> don't know what repo version means

repo = repositories, i.e. the online servers where you can download your packages from, normally with synaptic package manager (System --> Administration) or via CLI with "apt-get install" or "aptitude install".

From your ubuntu installation, while connected to the internet you should go to your synaptic manager, enable all the repositories (from setting) and try to install the package "nvidia-glx" or "nvidia-glx-new" (I am not sure which one supports your video card, but you can google it up, I suppose).

Synaptic (and the people behind it) make sure your dependencies are sorted out properly.

---

