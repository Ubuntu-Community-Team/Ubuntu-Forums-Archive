---
title: "[SOLVED] Can't boot Ubuntu"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Yoke &amp; Chung on 2007-12-08
Hi,

I am trying to install Ubuntu on another PC, but Ubuntu fails to load after installation and I have this message:

"Error loading operating system"

Booting from liveCD is ok, and the installation process is smooth with both 7.04 and 7.10, however, the computer just wouldn't boot from hard disk after the installation process is over.

My hardware setting is as follows:

1. AMD Sempron 2600+
2. FOXCONN 6100K8MB-RS motherboard with built-in ethernet, and nVidia 6100 graphics.
3. 1 GB (3 x 512MB) DDR RAM
4. 80GB Maxtor SATA HDD

Anyone with any idea? 

Thanks in advance.

---

### Post by LaRoza on 2007-12-08
Try reinstalling grub.

---

### Post by Yoke &amp; Chung on 2007-12-08
Sorry, please pardon my ignorance, how do I re-install grub?
I have been installing Ubuntu from CD a few times, and still face the same problem.

Thanks for your quick response.

---

### Post by PmDematagoda on 2007-12-08
Try using [Super GRUB]("http://supergrub.forjamari.linex.org/?section=download") to see if you can fix GRUB using it.

---

### Post by Yoke &amp; Chung on 2007-12-08
Thanks, will try the "super grub"

---

### Post by Yoke &amp; Chung on 2007-12-09
Hi all,

Tried super grub, managed to boot to ubuntu from the super grub, also I tried booting from first hard disk option from Ubuntu LiveCD, managed to boot from hard disk as well. However, still cannot boot directly from the hard disk, even after using super grub to fix the boot sector.

Could be the hard disk problem, let me try a few other options and will update the outcome to share with fellow forum users.

Thanks and regards

---

### Post by Yoke &amp; Chung on 2007-12-20
Finally the problem is solved. I did not mention my setup has an IDE drive configured as slave (containing only data) as I thought it is not important. 

However, after spending hours troubleshooting including numerous re-installation, the problem was actually due to the IDE drive. Somehow Ubuntu will try to boot from the IDE, I don't know why, even though the SATA drive is primary master. After removing the cables to IDE drive, GRUB was able to start automatically, however, Ubuntu still could not start. I gotta do another installation (with IDE drive unplugged), and finally I got a working system :)

I connected the IDE drive back to my computer after I got a running system, and so far it has not given me any problems yet, and the computer is booting up fine. (Keeping fingers crossed).

---

