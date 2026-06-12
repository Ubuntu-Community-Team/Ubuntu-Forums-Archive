---
title: "Another way to install Ubuntu?"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by Ludwig7666 on 2006-08-18
Hi.

I was wondering if there is another way to install Ubuntu on another low end machine? I can get the Live CD to install but when I go to install it onto the HDD it don't open the install program.

system specs:

Dell desktop
Old OS is windows 98
CPU: Pentium 3, 500 to 600 MHZ. Don't recall the actuall speed.
Mem: 160. not sure wich kind of mem or speed.
think it's a 3GB HDD.
1 CD Rom and 1 Floppy drive.
Onboard sound and video cards.
Dial-up nic

It loads up somewhat fast but when it's done it slows way down. Also I can't open anything or even the install thing from the desktop to partition it. Then I tried Debian. It I guess installed but I don't see any desktop at all. It's just all command line. Or am I missing something from Debian? I havn't used or seen anything from or of it. Just downloaded to try myself for future. So does it have a desktop like Ubuntu?

---

### Post by Arisna on 2006-08-18
You can use the Alternate installation CD for Ubuntu to install in text mode and add a desktop later.

It would also be possible for you to put a desktop environment on that Debian installation you did, if you want to keep it. The command `aptitude install [name of package]' should work as in Ubuntu, but on Debian you would first switch to the root (administrator) user the "traditional" way using the command `su' and typing in your root password, as opposed to prefixing the command with "sudo" to gain root access for just that command.

---

### Post by unisol on 2006-08-18
download or purchase the alternate-install cdrom, its for systems with less than 192 mb of ram, it installs in text mude and is much more stable. if it still wont install consider xubuntu with the xfce desktopmanager good luck hope it will help

---

