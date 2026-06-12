---
title: "Booting Ubuntu 8.10 on a macbook 3,1"
date: 2008-12-16
forum: Apple Hardware Users
---

### Post by Keyblade92 on 2008-12-16
Right, I installed ubuntu on the macbook, after creating a second partition. However, the macbook boot loader doesn't recognize the ubuntu bit, and it only boots into Leopard - does anybody know how to fix this? I've never really messed around with the boot loader, so I'm quite cautious.

Thanks,
David

---

### Post by shadowdude1794 on 2008-12-16
You need to get [rEFIt]("http://refit.sourceforge.net/"), and either install it or burn a CD. It should solve your problem.

---

### Post by cyberdork33 on 2008-12-16
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by Keyblade92 on 2008-12-17
> **shadowdude1794 said:**
> You need to get [rEFIt]("http://refit.sourceforge.net/"), and either install it or burn a CD. It should solve your problem.

I installed it onto the Mac HD, but I still get no menu when I boot up, and end up in the mac os.

---

### Post by beauman on 2008-12-17
Did you run the installation script under OS X in a terminal? Then use the partition tool from rEFIt (at the boot menu) to sync rEFIt with the MBR of your linux partition. If you don't have an english keyboard, "Y" and "Z" may be swapped. Did you install grub  in the MBR of the linux partition (not in the MBR of the HD)?

see also:
[OS X and Ubuntu dual boot]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation#OS%20X%20and%20Ubuntu%20dual%20boot")

Note that the documentation for Intel CPU-based Macintosh hardware is about to be restructured at the moment. You should be able to acces the right wiki for you at the [MacBook start page]("https://help.ubuntu.com/community/MacBook").

---

### Post by cyberdork33 on 2008-12-17
> **Keyblade92 said:**
> I installed it onto the Mac HD, but I still get no menu when I boot up, and end up in the mac os.
[http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

---

