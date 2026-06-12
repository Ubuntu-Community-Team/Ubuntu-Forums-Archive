---
title: "Deleting windows"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by 2k1stang on 2007-04-30
I've searched around and tried a couple things, but I can't figure it out. I'm totally new to Ubuntu (just installed it last week) but I don't feel the need for Windows anymore. Like I said, I'm new so if someone could give me a detailed description of what to do, I would really appreciate it. :redface:

---

### Post by taurus on 2007-04-30
You can install gparted and use it to format the partition Windows is on.  Then, Windows will no longer be on your machine.

```
sudo aptitude update
sudo aptitude install gparted
gksudo gparted
```

---

### Post by whee on 2007-04-30
It is possible to wipe your entire Windows partition with the liveCD of gParted, then you can add the new free space with gParted to your Ubuntu installation.
Though i don't know if this would delete the Windows entry from Grub though.

---

### Post by lakersforce on 2007-04-30
Alternatively you can reinstall lunix.

---

