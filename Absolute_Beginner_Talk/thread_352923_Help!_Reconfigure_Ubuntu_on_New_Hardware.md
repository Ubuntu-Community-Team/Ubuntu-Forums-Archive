---
title: "Help! Reconfigure Ubuntu on New Hardware"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by grif2k1 on 2007-02-03
To anyone:

I transferred my SATA HD with a working Ubuntu Edgy installation to another PC with different CPU, video card etc. Obviously it will not find the previous hardware and will spew a lot of errors upon boot-up. Is there a way to force Ubuntu to "recalibrate/reconfigure" itself whether within the current installation (command line), or do I have to reinstall everything from CD (from scratch)? Will reinstalling from CD recognize the previous installation and repair itself, thus preserving my files?

Thank you for any advice you can provide.

---

### Post by neverett on 2007-02-04
I would say it depends on your experience.  If you are experienced, you could probably find enough help on the web to help you correct the errors.  However, if you have very little Linux/Ubuntu experience, then I would recommend a clean installation.  If your computer will boot Ubuntu, I would strongly recommend backing up all of your important files including your configurations.

---

### Post by The Noble on 2007-02-04
Yes, xorg is probably where most of your problems are. You can reconfigure it by using 
```

sudo dpkg-reconfigure xserver-xorg

```
in the console. You can basically use all of the defaults it gives you unless you know what to change. Otherwise, the linux kernel is dynamic and should not cause any errors (if it did have errors, it won't boot in the first place).

---

