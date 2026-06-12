---
title: "Dual Boot two linuxes"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by satbunny on 2006-10-18
Ok. I have a machine booting Ubuntu. I'd like to dual boot Ubuntu and PCLinuxOS. Ubuntu uses Grub, PCLinuxOS43 uses Lilo.

How do I do it?

---

### Post by pbaehr on 2006-10-18
Whichever you install second (probably PCLinuxOS, since you already have Ubuntu running) will take over the master boot record with their boot loader. Lilo should still be able to launch your Ubuntu partition. I'm not sure if it will automatically detect it or if it will need manual configuration since I've never done a PCLinux install.

Alternatively, if you prefer Grub you can always install it after you're done and overwrite whatever is currently there.

There may also be an option to not install a boot loader at all for PCLinux in which case you'll just need to manually add it to your existing Grub menu which is on your Ubuntu partition.

But it shouldn't matter. Both Grub and Lilo should be able to load both distros.

---

### Post by PriceChild on 2006-10-18
check out [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html) to reinstall your grub if you want to.

---

### Post by mofokuban on 2006-11-20
Ah, it's a good thing I searched the forum about this before I decided to post; I was going to ask the same question!

I have tried this, and yes, you must manually add Ubuntu to the Grub and/or Lilo menu when setting up, but the past few times I've done that, it causes Ubuntu to have errors (i.e., no sound, drivers are bad, etc.).

So, what would more knowledgeable Ubuntu/Linux users suggest?

I'm thinking that installing PCLinuxOS on the remaining 50GB of my hard drive and then reinstalling Grub with Ubuntu should work.

What do others think about that?  Would it work?

---

### Post by Xappe on 2006-11-20
I'm not too familiar with lilo, but for two distributions using grub, I usually put my main distribution's grub on the mbr and, if possible, the other distribution's grub on the root partition of that particular distribution 

(for ubuntu this can be achieved with the alternate install cd where you get the option to choose where to install grub) 

This way you get two independent grub menus that you link together with the chainload option in the first grub menu (the one on the mbr).

This is very handy when the second distribution is in development and get lots of kernel upgrades since you don't have to bother about changing the kernel entries in your main grub menu :)

---

### Post by glotz on 2006-11-20
Yes, it would work.

---

