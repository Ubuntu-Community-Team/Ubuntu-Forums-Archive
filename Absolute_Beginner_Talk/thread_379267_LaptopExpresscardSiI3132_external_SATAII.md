---
title: "Laptop/Expresscard/SiI3132 external SATAII"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by dj9866 on 2007-03-08
Can anyone provide some guidance on how to make the following work?

     HP dv8000us laptop...AMD Turion(64 bit)...Ubuntu 6.10-32 bit
     Expresscard SATAII adapter...Sil3132 chip
     External SATAII enclosure

Being a new Ubuntu user, I am at a loss as how to begin working on this problem.  The Silicon Image website has drivers for Fedora Core 2/3/4 (32 bit drivers for AMD and EMT64T platforms), Red Hat Enterprise Linux 4.0 Updates 1/2/3, SuSE Enterprise 9.0, SP1/2/3, SuSE Pro 9.3.  Are any of these drivers usable to me?

Any suggestions will be greatly appreciated.

---

### Post by Drizzt321 on 2007-08-05
Hopefully you've gotten it working before this, but just in case, I have the exact same card and it works perfectly under Linux. All you need to do is load the drivers from the kernel as they most likely have been compiled as a module. You probably will also need to load the pciehp or the acpiphp hot plug drivers, or failing both those methods, boot Linux with the card in to get it working. It all depends on your system BIOS if it has the correct method or not for PCI-Express hotplug.

--Aaron

---

### Post by getsome831 on 2008-02-20
So i have this exact same issue, how exactly do i "load the drivers from the kernel", sorry...i'm a total noob.  Got anything like a set of steps i could follow?

Thanks.

---

