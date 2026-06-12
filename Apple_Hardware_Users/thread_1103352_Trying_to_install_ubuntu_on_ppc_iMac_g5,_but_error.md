---
title: "Trying to install ubuntu on ppc iMac g5, but error at the last second"
date: 2009-03-22
forum: Apple Hardware Users
---

### Post by dobelini303 on 2009-03-22
Hello,
I recently aquired an old iMac PPC g5. I figured, lets re-install OSX, re-partition it so that Mac OSX has about 17 GB and Ubuntu gets the rest. I did that, got a copy of Ubuntu ppc, booted from it, ran the installer and everything was fine. Except. At about 94%, it was installing the bootloader and told me that I didn't have some special Apple partition or something (I didn't read the message thoroughly). The installer quit. I tried again with the same settings I wanted, and still, same error. What did I do wrong?

---

### Post by tiresia on 2009-03-22
How did you install Ubuntu? The iMac G5 is a 64bit machine, did you choose powerpc64?

---

### Post by dobelini303 on 2009-03-22
Aha!
I think that's the problem, but I'm not sure. I wasn't really paying attention when I burned it. Thanks. :D

---

### Post by dobelini303 on 2009-03-22
Alright, another problem. Now that I got the 64bit version of Ubuntu PPC burned onto a CD, my iMac won't boot from it. What else did I do wrong?

EDIT: Or should I use the minimal version and cli? That would be easier, I think.

---

### Post by tiresia on 2009-03-23
Ok,  maybe I was not clear in my post. There is just one PPC Ubuntu Installer (for both architecture, ppc32 and ppc64). When you boot from the CD, hit TAB to see the different options you have. You must choose a 64bit option. 
If you are trying to install from the live CD (Ubuntu Hardy 8.04) try for example ```
live-nosplash-powerpc64
```

---

