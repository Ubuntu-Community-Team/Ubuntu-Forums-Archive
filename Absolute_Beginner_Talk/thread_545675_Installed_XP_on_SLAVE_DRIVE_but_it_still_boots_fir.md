---
title: "Installed XP on SLAVE DRIVE but it still boots first"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by dez_cole on 2007-09-07
So I have Ubuntu as my primary OS, but I decided to install Xp again for music production purposes. When I installed Xp I installed it on a second hard drive. I unplugged the Ubuntu drive to make sure MBR didn't replace GRUB. Everything went well until I connected the Ubuntu drive as master and the Xp drive as slave. Even though Xp is slave it still boots first...

The Ubuntu drive works perfectly on its own, the jumper pins on both hard drives are set as Master(linux) and Slave(Xp)

I'm almost definitely sure the bios settings are correct but I'll check once more after I post this.

I don't know how to fix this, should I install grub onto Xp, and if yes how should I go about this?

Thanks!

Ps. Could this just be a case of Windows being extremely greedy?(seems like it)

---

### Post by louieb on 2007-09-08
Just one thought. Check your BIOS setup and make sure the Ubuntu drive is 1st in the boot order. Can't think of any other reason the PC would boot the XP drive before the Master drive.

---

