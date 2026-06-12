---
title: "X server help"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by petersonjacob on 2008-01-01
finally got my setup complete, but now my card wont achieve anything higher than 800x600 and my NVIDIA Xserver Settings says, "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. i did what it said to do and it said new xorg, making backup and writing to new xorg, how do i overcome this problem? (using a 6200 GeForce) and have nvidia-glx-new and nvidia-kernel-common installed.

---

### Post by RomeReactor on 2008-01-01
Hi. Please post the output of:
```
cat /etc/X11/xorg.conf | grep Driver
```

---

