---
title: "no nvidia driver after ubuntu upgrade"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by jmagnuss on 2007-01-07
I upgraded ubuntu and now my x won't start with the nvidia driver, it can't be found.  I tried removing nvidia-glx and adding it again, but lsmod|grep nv shows nothing.  I believe I need to use nvidia instead of nv because I'm doing dual screens with my tv.  Can anyone help me get that nvidia driver installed?

Thanks!

---

### Post by pay on 2007-01-07
Try ```
sudo aptitude install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
gksudo gedit /etc/X11/xorg.conf
```And change nv with nvidia

---

### Post by tseliot on 2007-01-07
Try this:
```
sudo aptitude install linux-restricted-modules-`uname -r`
```

If you installed the nvidia driver from the installer on Nvidia's website, try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by jmagnuss on 2007-01-07
envy fixed it, thanks!

---

