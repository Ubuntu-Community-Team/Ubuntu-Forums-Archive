---
title: "slow GRUB"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by An_Dynas on 2008-01-10
I have recently installed Xubuntu 7.10 to an older machine.  Xubuntu is running great when I can finally get to it.  The problem is that the GRUB startup is excruciatingly slow (11-13 mins.) before it will get to the Xubuntu startup screen.

This is a dedicated linux machine so I really don't need GRUB.  I understand that I can't get rid of it, maybe can I bypass it?  Any suggestions?

---

### Post by LaRoza on 2008-01-10
Grub is the boot loader, and you do need it (or at least, a bootloader)

Post your specs, otherwise we can only speculate.

---

### Post by eolson on 2008-01-10
I had the same problem on my laptop.   Found the fix here

[http://ubuntuforums.org/showthread.php?t=580903&highlight=ubuntu+slow+boot](http://ubuntuforums.org/showthread.php?t=580903&highlight=ubuntu+slow+boot)

---

### Post by philinux on 2008-01-10
Follow the link for known bugs.

---

### Post by An_Dynas on 2008-01-10
Thanks everyone.  I had tried the "quiet splash" route when it was loaded with Fluxbuntu.  It wouldn't boot at all after that, so I installed this distro of Xubuntu -- same GRUB problem, but I'll try it again.  Appreciate the responses.

BTW, my specs are Pentium 550 mhz with 128 memory (Xubuntu runs surprisingly well).  What else do you need to know?

Would anyone recommend a complete re-install/re-partition since the system appears to have inherited whatever hang-up it had from the last install?

---

### Post by philinux on 2008-01-10
Grub wont be slowing things down it's the loading of boot files and drivers.

If you've now got text messages scrolling up the screen you should be able to see whats causing the hangup.

---

