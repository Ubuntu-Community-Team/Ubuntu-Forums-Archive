---
title: "GRUB... error 18"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2007-03-25
Hi,

I just tried installing Feisty on my IBM thinkpad (X31), but when I try to restart nothing happens.  The following message appears...

GRUB loading stage 1.5.

Grub loading, please wait...
Error 18

Any help will be greatly appreciated... I have a uni project I need to finish.

Cheers

---

### Post by Twig E. Pottox on 2007-03-25
your bios is older and your hdd is newer or larger .  I had the same problem , solved it by partitioning the boot drive to a size  under 8 gb. if your system is older you may have to get more clever . google  grub error 18 and you will see several better explainations and good luck the easy one did it forme

---

### Post by igknighted on 2007-03-25
You can create a small partition for the /boot section at the front of your drive.  When you do the install, create an extra REALLY SMALL (512 MB max is all you need, and could do with far less I'm sure) partition in the first spot on the disk.  Then when you get to mount points call it /boot.  This way your boot data is where the drive/bios needs it, but feisty doesn't have to be there.

---

