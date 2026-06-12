---
title: "Installed ubuntu successfully alongside Leopard, but having booting issues"
date: 2010-09-20
forum: Apple Hardware Users
---

### Post by tito jackson on 2010-09-20
So I used boot camp assistant to create a partition and then successfully installed 10.10 beta alongside Leopard, but I forgot to tell the installer which partition to install grub into so now I'm left with Grub loading by default when I turn the computer on.

This would be fine except I can't load up Leopard from Grub. The only way I can get into the Mac OS now is to hold ALT while booting.

Is there a way I can remove Grub and or get it to use reFit instead?

Thanks in advance.

-Tito

---

### Post by pindar on 2010-09-21
> **tito jackson said:**
> So I used boot camp assistant to create a partition and then successfully installed 10.10 beta alongside Leopard, but I forgot to tell the installer which partition to install grub into so now I'm left with Grub loading by default when I turn the computer on.

This would be fine except I can't load up Leopard from Grub. The only way I can get into the Mac OS now is to hold ALT while booting.

Is there a way I can remove Grub and or get it to use reFit instead?

Thanks in advance.

-Tito
Try this: boot into Mac OS X. Go to "System Preferences", "Startup Volume" and select your OS X partition there. This should be enough to make OS X the default boot option. After that, you can either install refit or use the alt key to boot into Ubuntu. 

HTH

pindar

---

### Post by tito jackson on 2010-09-21
Pindar,

Thanks for the advice. Now when I boot up, it goes to the refit menu which shows me mac, ubuntu, and windows (which I believe was created by boot camp assistant, as there is no actual windows installed on the system).

Thanks again,

-Tito

---

