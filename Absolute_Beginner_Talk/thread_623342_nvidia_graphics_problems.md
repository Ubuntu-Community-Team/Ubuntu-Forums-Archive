---
title: "nvidia graphics problems"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by henryv_67 on 2007-11-25
hi, im new to ubuntu, and so far i have to say that i am impressed. anyways, i did a fresh install of 7.10 and i went to enable visual effects and it asks me to use the nvidia accelerated graphics driver. I enable this and restart. all of the sudden my graphics are all screwed up, text is missing from menus, images are distorted, all that stuff. So i have to reconfigure my xorg file to fix this. My question is, how do i fix this so the nvidia driver will work correctly? also, i have geforce2 mx integrated graphics. thanks!

---

### Post by jken146 on 2007-11-25
```
sudo dpkg-reconfigure xserver-xorg
```

I'm not sure about this, but I think GeForce 2 cards may need the legacy nVidia driver rather than the 'new' one.  Don't quote me on that though.

---

### Post by henryv_67 on 2007-11-25
yes, this is what i did. when the driver list comes up i select nv, not nvidia. if i select nvidia, then thats what messes up my graphics. so would there be any way to enable the effects?

---

### Post by PeterJS on 2007-11-25
How did you install the drivers in the first place? I've had a lot more success with the restricted drivers manager than with a manual install.

---

### Post by henryv_67 on 2007-11-25
ok i seem to have solved half of the problem. I've installed the legacy drivers and my graphics are back to normal, but when i go to enable the effects now, it uninstalls the legacy driver and installs the "newer" nvidia-glx driver. so how would i get it to use the legacy driver?

---

### Post by rubicon on 2007-11-25
> **henryv_67 said:**
> ok i seem to have solved half of the problem. I've installed the legacy drivers and my graphics are back to normal, but when i go to enable the effects now, it uninstalls the legacy driver and installs the "newer" nvidia-glx driver. so how would i get it to use the legacy driver?
I guess Compiz just needs nvidia-glx or nvidia-glx-new and doesn't support nvidia-glx-legacy. I've got the same problem with my GeForce 2 MX 400, and I think it's videocard-related problem: it is too old for compiz :)

---

### Post by FuturePilot on 2007-11-25
The GeForce2 is supported by the nvidia-glx driver. Also the nvidia-glx-legacy driver does not support compositing anyways.

---

