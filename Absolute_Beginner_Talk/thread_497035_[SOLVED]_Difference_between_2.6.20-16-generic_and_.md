---
title: "[SOLVED] Difference between 2.6.20-16-generic and 2.6.20-15-generic?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by keyboardashtray on 2007-07-09
Just out of curiosity, and because knowing is half the battle, why (on my dual boot) does it give me the option to start in  either 16-generic or 15-generic (and a safe mode for each)? I just go with 16 because it's the default, but I like to know why it even gives the option for 15, and my search didn't turn up any good explanation.

Thanks!

---

### Post by wormser on 2007-07-09
Every time you install a new kernel it is added to the list.  You can boot into either one.  Most recommendations are to keep at least 2 on the list in case you run into an issue with the latest kernel.  In order to remove or modify your Grub boot list edit /boot/grub/menu.lst.

---

### Post by lbelloq on 2007-07-09
Seems you updated you system recently.
GRUB gives that option because when you updated your system, Ubuntu downloaded and installed a new kernel, a more up-to-date version. But it keeps the old one (dunno why, maybe for compatibility reasons or because it simply does not erase the option of booting with the old kernel in GRUB) int he system and in the boot options.
I think you'll need to deelte the 15-related entries in GRUB, but I don't know exactly how to do it.

P.D.: Ah, thanks, wormser. That's it.

---

### Post by keyboardashtray on 2007-07-09
Thanks guys, I appreciate it! :)  I'll keep that other one on there, then, just to be safe.

---

### Post by Nekiruhs on 2007-07-09
> **lbelloq said:**
> Seems you updated you system recently.
GRUB gives that option because when you updated your system, Ubuntu downloaded and installed a new kernel, a more up-to-date version. But it keeps the old one (dunno why, maybe for compatibility reasons or because it simply does not erase the option of booting with the old kernel in GRUB) int he system and in the boot options.
I think you'll need to deelte the 15-related entries in GRUB, but I don't know exactly how to do it.

P.D.: Ah, thanks, wormser. That's it.
Yeah, I had to use it. Normally when I install the 6 kernal everytime it works. Last time though it didn't and the 15 kernel saved me.

---

