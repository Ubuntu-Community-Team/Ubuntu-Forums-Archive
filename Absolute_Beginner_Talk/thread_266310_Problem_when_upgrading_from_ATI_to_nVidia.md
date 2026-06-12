---
title: "Problem when upgrading from ATI to nVidia"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by Josh1 on 2006-09-27
Ok, so i turned off my pc, put in the nVidia 6600le, restarted and it said something about x-server not being able to load.. How do I put this back to defaults?
- Josh

---

### Post by Perfect Storm on 2006-09-27
Try with
```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by Josh1 on 2006-09-27
That fixed it, now I will try to install the nVidia drivers.
Thanks alot :D.

---

### Post by Perfect Storm on 2006-09-27
My pleasure ^_^

installing nvidia driver:
```
sudo aptitude install nvidia-glx
sudo nano /etc/X11/xorg.conf
```

in **Section "Device"** change "nv" to "nvidia"
save and exit <ctrl> + <o> | <ctrl> + <x>

restart x: <ctrl> + <alt> + <backspace>

---

### Post by Josh1 on 2006-09-27
> **Artificial Intelligence said:**
> My pleasure ^_^

installing nvidia driver:
```
sudo aptitude install nvidia-glx
sudo nano /etc/X11/xorg.conf
```

in **Section "Device"** change "nv" to "nvidia"
save and exit <ctrl> + <o> | <ctrl> + <x>

restart x: <ctrl> + <alt> + <backspace>

Damn... thankyou!! :D.
edit:
Oh gnoes, just reliased that my ALT+Tab decide to go AWOL, anyway of getting it back? :(.
edit2: Never mind, got it back :P

---

