---
title: "How to uninstall Ubuntu?"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by _d5 on 2007-10-11
I need to uninstall ubuntu. How to do that without messing up the GRUB loader and still be able to load Windows, which I already have installed???

Thank you in advance!

---

### Post by jordanmthomas on 2007-10-11
If you remove Ubuntu, GRUB will not be able to find its configuration file and you'll have problems booting.

What you can do, however, is to boot off a Windows CD and go to recovery mode and just type /FIXMBR.

After you do that, you can just remove your Ubuntu partition if you feel like it.

---

### Post by _d5 on 2007-10-11
Thank you, I will try!

What are the minimum requirements of Ubuntu, because I want to try to run it on a Virtual PC.

---

### Post by SuperDuck on 2007-10-11
> **_d5 said:**
> Thank you, I will try!

What are the minimum requirements of Ubuntu, because I want to try to run it on a Virtual PC.

From the Ubuntu site:

> System Requirements 
Ubuntu is available for PC, 64-Bit and Mac architectures. At least 256 MB of RAM is required to run the desktop install CD. Install requires at least 4 GB of disk space. 


---

