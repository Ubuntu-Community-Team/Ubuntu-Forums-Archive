---
title: "NVidia kernel module/ X module API mismatch"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Belkorin on 2007-07-03
Ubuntu 6.06 upgraded to a new kernel, and apparently, new nvidia drivers, and now when I try to start X I get a message about an API mismatch, saying the NVidia kernel module is version 1.0.8776 and the X module is version 1.0.7184 and I need to make sure that they're both the same or something like that. How do I get the X module updated to 1.0.8776? I've tried apt-get upgrade, and that didn't fix it.

---

### Post by Outrunner on 2007-07-04
I think you'll need to reinstall nvidia-kernel-common and possibly your nvidia drivers

```
sudo aptitude remove nvidia-kernel-common
```
```

sudo aptitude install nvidia-kernel-common

sudo aptitude install nvidia-glx
```

If you have a very old nvidia card, install the nvidia-glx-legacy drivers instead of the normal nvidia-glx.

---

