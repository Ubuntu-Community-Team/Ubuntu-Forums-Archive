---
title: "nvidia driver ???"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2006-10-19
i installed the nvidia driver from automatix.
i am running dapper with the latest updates.
how do i find out what nvidia card i have?
what driver i have?
if i upgrade to edgy eft will my xserver fail to work with the new kernel?
this happened once when i changed kernels/
how would i fix if this happened?
would it be better if i uninstalled the driver?
i think my card is some what old not the top of  the line maybe 16mb video ram or  so.

---

### Post by CatKiller on 2006-10-19
> **abu-fatu said:**
> how do i find out what nvidia card i have?

```
lspci | grep VGA
```

I'd only be speculating by answering any of the other questions.

---

### Post by ReaderRat on 2006-10-19
Please run this in Terminal::
```
sudo gedit /etc/x11/xorg.conf
```
and post the output here.

EDIT:  Nevermind....

---

### Post by CatKiller on 2006-10-19
> **ReaderRat said:**
> EDIT:  Nevermind....

Sorry. O:)

---

### Post by abu-fatu on 2006-10-19
0000:01:0 VGA compatible controller:nVidia corporation NV5M64 (RIVA TNT2 model 64/Model 64 Pro) rev 15

in xorg.conf ihave :
Identifier "Nvidia Corporation NV5M64 (RIVA TNT2 Model 64/Model 64Pro"
Driver "nvidia"

---

