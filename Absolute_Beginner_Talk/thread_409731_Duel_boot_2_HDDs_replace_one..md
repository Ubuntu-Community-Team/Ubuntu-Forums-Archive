---
title: "Duel boot 2 HDDs replace one."
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by DreamcastJack on 2007-04-14
okay, I'm duel booting Ubuntu 6.10 and Puppy 2.15CE.  I wanna  change out the Puppy HDD for another 40GB Hdd that I Have,  I wanna put Freespire 2.0 on it when its out.  will replaceing a Duel-Booted HDD mess my Edgy install up?  thanks.

---

### Post by BoneKracker on 2007-04-14
Probably not.  Not unless you are using a single bootloader MBR to boot both linuxes and it happens to be on the disk you are removing.

If you set each disk up with its own bootloader and are chainloading one from the other, then all you have to do is make sure the disk you are leaving in is designated in your bios (or firmware depending on what kind of machine you have) as the boot disk.

If you are using a single bootloader instance, and it is not on the disk you are leaving in, then you will have to run grub-install and update-grub, and also make sure your bios is set to boot from the disk you are leaving in.

---

