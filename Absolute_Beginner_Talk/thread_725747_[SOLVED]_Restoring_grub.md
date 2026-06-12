---
title: "[SOLVED] Restoring grub"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by maclee1988 on 2008-03-16
I have Ubuntu and Windows XP dual boot on my machine and I am using windows NT boot loader with the Grub loader on the Ubuntu partition. It worked fine. I currently resized my ubuntu partition with the GParted in the Ubuntu 7.10 install CD, and the ubuntu partition started not booting up and only shows me 'GRUB_' when I selected ubuntu in the NT loader. How can I get it work again?

---

### Post by zxscooby on 2008-03-16
you can reinstall grub using the alternate install cd recovery mode.
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)
or the super grub disk
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by sandysandy on 2008-03-16
have a look at this thread on how to re-install grub

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by maclee1988 on 2008-03-16
I followed the instructions but there were still errors. The grub loader changed the booting totally after I have done according to the post. The grub loader loaded instead of the windows NT loader on start up and told me it was not able to mount the partitions

'Error 17: Cannot mount selected partition

Press any key to continue...'


Then it redirected me to the NT loader when I selected in the grub menu

'Other operating systems:
Microsoft Windows XP'

Then in the NT loader menu, I selected Ubuntu, and when I selected Ubuntu on the menu, it show me 'GRUB_' again.

---

### Post by maclee1988 on 2008-03-16
I changed the device name in /etc/fstab and /boot/grub/menu.lst, as the device names changed after the resizing (I reformated one of the partitions)

Also I reinstalled grub on the ubuntu partition and the NT boot loader on the 1st partition, so everthing is okay now.

---

