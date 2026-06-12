---
title: "Kernerl and newbies"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by Vladimir_BG on 2006-04-16
I've been told that by upgrading the kernel to i686 my athlon 850MHz 256 MB ram, GF2 MX400 machine would get quite a boost.

Is it true?

By upgrading kernel will I compromise my system and package integrity?

Will I need to re-install nVidia legacy driver?

If the benefits are there, how do I do it?

---

### Post by htinn on 2006-04-16
I think you want the k7 kernel with that CPU. Kernel upgrades use more of your /boot partition (assuming you have it on a different partition), and require a restart. Otherwise, they're no big deal. I doubt you'd get much of a speed boost out of it, though.

It is a totally different kernel, so you'd have to reinstall the video driver (and anything else that needs a special kernel module), afterward.

---

### Post by Mustard on 2006-04-16
I think you will find the difference to be minimal to negligible.  You would need to install the linux-restricted-module for you kernel version for your nvidia drivers to work (assuming you are using the nvidia-glx drivers).

You can find your current kernel version with the uname -r command.

---

