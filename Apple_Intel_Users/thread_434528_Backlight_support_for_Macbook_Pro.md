---
title: "Backlight support for Macbook Pro"
date: 2007-05-06
forum: Apple Intel Users
---

### Post by Tyrdium on 2007-05-06
It works! Well, via command line.

```
sudo aptitude install build-essentials
sudo aptitude install subversion
svn co https://svn.sourceforge.net/svnroot/mactel-linux/trunk/tools/
sudo aptitude install pciutils-dev
sudo aptitude install zlib1g-dev
cd tools/backlight
gedit Makefile, change *gcc $(CFLAGS) $^ -o $@ $(LIBS)* to *gcc $(CFLAGS) $^ -o $@ $(LIBS) -lz*
make
sudo make install
```

Type *backlight* alone to find the current setting for your backlight. *backlight +10* will increase it by 10 units, *backlight -10* will decrease it by 10 units. Go too low, and your backlight will turn off completely. I find I can't go any lower than 40 units.

Enjoy!

---

