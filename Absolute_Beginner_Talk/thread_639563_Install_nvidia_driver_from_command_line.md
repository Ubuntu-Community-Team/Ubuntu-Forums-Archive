---
title: "Install nvidia driver from command line"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by helino on 2007-12-13
Hi,

I'm trying to install the nvidia driver from the command line. I've done:
```

sudo apt-get install nvidia-glx-new
sudo apt-get install linux-restricted-modules
sudo nvidia-xconfig

```

But when I start X, it won't start. It says that it found screens, but not any with the right configuration?

I'm using 7.10 server install with fluxbox

I'm grateful for any help

---

### Post by Dr Small on 2007-12-13
Perhaps you could try reconfiguring X ?
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by helino on 2007-12-13
I've tried to reconfigure xorg, but it doesn't help. The strange is that I get it working on this computer when I used graphical installer...

---

