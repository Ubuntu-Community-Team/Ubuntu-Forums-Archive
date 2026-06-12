---
title: "how to reset xorg.conf"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by kane77 on 2007-03-29
how do I make dpkg-reconfigure xserver.xorg autodetect settings?? 
It auto detected first time, but then I installed nvidia drivers and it only gave me Generic adapter etc... 
I already uninstalled the nvidia drivers but now I cant get it back to autodetecting  ....

and my screen is a mess (maximum 50Hz refresh rate... weird resolution...)

---

### Post by bodhi.zazen on 2007-03-29
> **kane77 said:**
> how do I make dpkg-reconfigure xserver.xorg autodetect settings?? 
It auto detected first time, but then I installed nvidia drivers and it only gave me Generic adapter etc... 
I already uninstalled the nvidia drivers but now I cant get it back to autodetecting  ....

and my screen is a mess (maximum 50Hz refresh rate... weird resolution...)

Did you try the nvidia driver ?

If not, start with that, 

Enter :

```
gksudo nvidia-settings
``` and adjust your monitor from there.

If that fails, is there a backup xorg.conf ?

If not, use this : ```
sudo dpkg-reconfigure xserver-xorg
```

---

