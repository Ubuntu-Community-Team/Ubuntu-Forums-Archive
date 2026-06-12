---
title: "uninstall Ubuntu 10.10 and install Ubuntu 12.04 on Macbook pro with dual boot"
date: 2013-06-29
forum: Apple Hardware Users
---

### Post by mysydney on 2013-06-29
My current Macbook pro 6.2 is dual booted for OSX 10.6.8 and Ubuntu 10.10 with rEFIt. I want to uninstall Ubuntu 10.10 and do a clean install of Ubuntu 12.04. Would you please help me to show how to do this step by step? Many thanks!
Joe

---

### Post by rkmugen on 2013-06-29
I'd love to help you, but I don't own any intel macs... though, having said that, presumably all you'd need to do is boot off of your 12.04 disc (or USB flashdrive, if you've burned the ISO onto one...) and proceed with the installation.

To boot off of the 12.04 CD (or DVD, if you burned it onto a DVD), just insert the disc into your MacBook, and reboot while holding either the 'c' or 'd' key.
To boot off of the USB flash drive, presumably for Intel machines, you simply need to insert the drive, reboot, and hold down the 'Option' key until you get the choice to select which drive you want to boot off of (i believe Intel MacBooks should be capable of this...).

In either case, after you've booted into 12.04 (I'm assuming you burned the live desktop ISO image), you simply need to double-click the 'Install Ubuntu 12.04" icon on the desktop.  It'll give you the option to replace 10.04 and not touch your 10.6.8 partition... though... it would still be able to set up the bootloader in such a way that when you boot it should still give you the option to choose which OS you want to boot into, every time you turn on your MacBook.... just like in 10.04.  Just be extra careful that you don't select the option that wipes the ENTIRE hard disk, or you'd be in for a seriously long chore of installing EVERYTHING from scratch (i hope you have your OSX installation/recovery media just in case).

---

### Post by mysydney on 2013-06-30
Thank you very much!

---

