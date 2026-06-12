---
title: "[resolved] make-kpkg problems - cannot boot kernels"
date: 2004-12-28
forum: Apple PPC Users
---

### Post by robsta on 2004-12-28
Hi, 

back then with debian sid make-kpkg always worked flawlessly for me.
Now on ubuntu every single kernel i'm building fails on bootup with the message:

"cannot open /lib/modules/x.y.z/modules.dep"

Lines containing this error are filling the screen for a few seconds, then it stops and says the system will reboot in 180 secs.

I also tried to compile reiserfs (which is on my /) support into the kernel instead of building the module (default setting).

Thanks for any advice, 
Rob

---

### Post by robsta on 2004-12-28
Heh, ok, seems like one needs to use kpkg with --initrd even when only recompiling the original ubuntu sources with the shipped .config. Using the initrd from the shipped kernel does not work ...

- rob

---

