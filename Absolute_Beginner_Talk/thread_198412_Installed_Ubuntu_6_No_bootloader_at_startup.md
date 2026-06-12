---
title: "Installed Ubuntu 6: No bootloader at startup?"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by mrmorris on 2006-06-17
Although I am fairly certain I saw Ubuntu write that it was installing Grub on HD0 during the last phase of the install, my system boots directly into Windows.

I should mention that my primary/previous system is WinXP from a hardware (NForce4) RAID 1 pair of discs. I have another discs (non RAID) which is where I installed Ubuntu to. So perhaps Ubuntu errornously designated Grub to a non-bootup disc? If I try to change the default boot-up disc in my bios, I will see Grub trying to load but it will fail.

So if Ubunto did install the bootloader wrong, what can I do?

Can I somehow install another bootloader from windows or manipulate Windows boot.ini file? Or can I bootup with the Ubuntu liveCD and change some config file to correctly point to my RAID1 Windows partition?

Help greatly appreciated,
Casper

---

### Post by %hMa@?b&lt;C on 2006-06-17
you could make a GRUB boot floppy

---

### Post by mrmorris on 2006-06-17
I got rid of the dreadfull floppy drive 6-7 years ago, my motherboard does not even have a controller.

---

