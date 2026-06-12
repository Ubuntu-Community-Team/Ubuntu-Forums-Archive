---
title: "Grub Error 22"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-02-22
I have a laptop here with windows xp on it, I installed edgy and everything was set up nicely for dual booting.

Then we decided to remove edgy (in order to reinstall), so we deleted the ubuntu partition and merged the free space with with the windows partition.

Upon restarting Grub gave an **Error 22**.

I tried searching the forum, but in most cases people had deleted their windows partition, ours is the opposite case.

Am I correct in assuming that Grub needs to edited to not look for the no longer existing Edgy partition? If yes, how do I fix this?

Thanks.

---

### Post by logos34 on 2007-02-22
There's nothing left to edit--it was on the ubuntu partition you deleted.  When you bootup, Grub stage1 on the mbr looks for your / (or /boot) partition for the config file (menu.lst) but you erased ubuntu, so you just get the error.  

If you want to be able to get into windows in the meantime until you reinstall ubuntu you can restore the win bootloader by booting into the recovery console from the windows install cd and going through the 'fixmbr' procedure.

---

### Post by PartisanEntity on 2007-02-22
Thanks for the tip, it worked, now we are installing Edgy again.

---

