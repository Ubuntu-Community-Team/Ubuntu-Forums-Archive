---
title: "install"
date: 2012-09-25
forum: Any Other OS
---

### Post by qa1433 on 2012-09-25
Hello,I'm trying to install winxp back on my lap top,it has a full install (mint 10)and the problem I'm have is the rescue grub keeps blocking the install or partition. What do I need to do?

---

### Post by daslinkard on 2012-09-25
Personally I think your problem is windows in general...the other problem if I'm not mistaken is that Windows likes to be installed 1st and then Linux or in your case Mint.  I've tried many distros of Linux and my heart belongs to Ubuntu.

---

### Post by qa1433 on 2012-09-25
Thank you! I'M having the same problem with Parted Magic also though.

---

### Post by oldfred on 2012-09-25
Moved to other OS as Windows & Mint.

Windows will only install to a primary partition (sda1 thru sda4) formatted NTFS with the boot flag (or active partition in Windows).

---

### Post by qa1433 on 2012-09-28
Thank you oldfred as usual, I over looked the obvious.

---

### Post by Bachstelze on 2012-09-28
If you want to completely replace Ubuntu with Win XP, you need to also delete the part of GRUB that sits on the MBR of your drive. Boot from the XP CD and enter a revovery console. Then run the commands FIXBOOT and/or FIXMBR.

---

