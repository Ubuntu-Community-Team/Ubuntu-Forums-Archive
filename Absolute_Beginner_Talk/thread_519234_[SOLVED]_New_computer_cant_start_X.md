---
title: "[SOLVED] New computer cant start X"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by hackle577 on 2007-08-06
I just got my new computer set up today and installed Feisty, but on boot I get an error that tells me X failed to start. Looking at the X server output, I get this:

```
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
No screens found.
```

My vid card is an nVidia GeForce 7300GS if that helps. Thanks a ton!

---

### Post by tgm4883 on 2007-08-06
did you try to install the nvidia drivers (and if so how?) or edit the /etc/xorg.conf file in any way?

I have the same card and it works nicely

---

### Post by hackle577 on 2007-08-06
Yeah, I installed nvidia-glx-new and everything's fine now.

---

