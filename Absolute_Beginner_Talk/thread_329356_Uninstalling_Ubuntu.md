---
title: "Uninstalling Ubuntu"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by bacladantu on 2007-01-01
I want to remove my old linux slave drive to intall a larger hard drive and just stay with windows XP. I cannot figure out how uninstall ubuntu so that the grub will allow windows to boot.

---

### Post by raul_ on 2007-01-01
[http://www.ubuntuforums.org/showthread.php?t=328441]("http://www.ubuntuforums.org/showthread.php?t=328441")

read the entire thread

---

### Post by oilchangeguy on 2007-01-01
you don't need to uninstall anything. just make sure the bios is set to boot from the cd drive and drop in the factory restore disc or your windows disc and you're ready to go. any reason you're giving up on ubuntu?

---

### Post by dfm21 on 2007-01-01
You can reinstall the default windows bootloader with **fixmbr** or **fixboot**. If you have XP professional, you are ready to go. Just boot the CD, drop to the recovery console, enter **fixmbr** and possibly **fixboot** (I don't know the difference) and the default windows bootloader should be on the hard disk you are booting from again. If you do not own a copy of XP pro, you can download both tools -> google.
Why do you want to uninstall Ubuntu? Just leave it on your small slave! ;)

---

### Post by oilchangeguy on 2007-01-01
try this, from the bios go to the boot tab and make sure hd 0 is set to boot before any other hd. and as long as your windows drive has not been altered in any way it should boot ok.

---

### Post by Mazen on 2007-01-01
You don't even need to do recovery just go through the setup of windows and at the end where it asks you to choose a partition just exit it ( F3 F3) and your boot loader should already be on ur drive.
Again, any given reason y ur uninstalling Ubuntu?

---

