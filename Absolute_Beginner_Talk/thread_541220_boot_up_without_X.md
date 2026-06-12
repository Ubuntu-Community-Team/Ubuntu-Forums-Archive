---
title: "boot up without X"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Snodgrass on 2007-09-02
How to boot up without X? I'm trying to install an update for an  Nvidia driver, and the program won't run within X.

---

### Post by Bachstelze on 2007-09-02
```
sudo /etc/init.d/gdm stop
```

will stop X and let you install your nvidia drivers. "start" will restart it.

---

### Post by banewman on 2007-09-02
If you use the recovery option you get only a command prompt. :)

---

### Post by InGunsWeTrust on 2007-09-02
when the the grub boot loader is loading select the ubuntu partition you want to start in and press e. You are presented with a list of items in the boot configuration. Select the longest line I think it starts with "kernel" at the end of the line type "linux single" without the quotes then press enter. With the line you just edited highlighted press b to boot from it. You will be dropped to a command line with root@yourcomputer name. Run the program you need to run but do not use "sudo" because you are already root.

---

### Post by InGunsWeTrust on 2007-09-02
> **banewman said:**
> If you use the recovery option you get only a command prompt. :)

recovery mode doesn't allow all linux commands I don't think. booting in single user mode will give you full functionality but no GUI

---

### Post by Bachstelze on 2007-09-02
You are both wrong. First, what Ubuntu calls the "Recovery mode" is in fact the single-user mode, the very same thing you get by adding "single" to your kernel boot parameters. And the nvidia drivers won't install in single-user mode.

---

### Post by banewman on 2007-09-02
sudo apt-get install & sudo dpkg-reconfigure xserver-xorg both work from the recovery option.

---

