---
title: "Grub Dual Boot Menu"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-02-13
I have just installed ubuntu, and am dual booting with windows xp. I noticed on the GRUB menu that the ubuntu was listed twice. It looks something like the following:


Ubuntu  <some numbers here>
Ubuntu (safe mode)
Ubuntu <some numbers here>
Ubuntu (safe mode)
Ubuntu memtest+
Other O/S
Windows XP

The numbers that are with Ubuntu are the same on both options.
I was wondering why this is? Is Ubuntu saving some previous session?

I managed to go to the menu.lst file in the /boot/grub directory and "comment out" the second menu options and they no longer show.

If Ubuntu is saving some previous session is it possible to configure ubuntu not to do this?

---

### Post by taurus on 2007-02-13
I bet you have both i386 and generic kernels in there.  If you want to use the generic only, then you can place a # in front of the lines for i386 to comment them out.  Or if you only use the i386 kernel, then do the same for the generic kernel.

And yes, each time you install or upgrade your kernel, it will add two entries for the latest one, kernel and recovery mode.

---

### Post by noorez on 2007-02-13
Hmm.....This is the first time i've put linux on my computer...and I remember doing a default installation.....so then that puts both i386 and generic kernels in? What is the difference between the two?

Also, what counts as upgrading the kernel?

---

### Post by taurus on 2007-02-13
If you installed it from a CD, then it came with the generic kernel.  I bet you got the i386 when you tried to install a driver, legacy, for your graphic card!

---

### Post by mikewhatever on 2007-02-13
Welcome to the forums. There has been a kernel update, during the last weekend or so. An update is kind of the a to put it, but in fact, we got the whole new kernel, while the older version is still intact and usable. If you look at the numbers in the boot menu, they probably are similar to this:
2.6.17-11
2.6.17-11 recovery mode
2.6.17-10
2.6.17-10 recovery mode

The first two are the newer ones, while the other two are the older. The older versions are kept, because sometimes, the newer ones do not work after the update. Many users have experienced graphic drivers problems, as numerous posts of the last few days show.

---

