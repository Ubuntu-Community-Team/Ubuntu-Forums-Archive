---
title: "[SOLVED] asus drivers"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Riffer on 2007-12-16
I've downloaded linux drivers from ASUS for my MB.  Its one of these .run type packages.  So I have a couple of questions.

There are 2 chipsets packages, one for 32 bit and the other for 64.  I run gutsy 32 bit generic on a AMD64.  Which chipset should I use?  I bet its the 64 bit one.

Next I can't figure out how to run the installer.  Its a ".run" installer, I've tried running it in terminal but I get back a "command not found".  Any ideas?

---

### Post by taurus on 2007-12-16
You need to be in the same directory that you have saved the .run file.  Also, make sure it has an executable permission.

```
chmod 755 **filename**.run
sudo ./**filename**.run
```

---

