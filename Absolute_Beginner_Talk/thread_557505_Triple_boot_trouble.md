---
title: "Triple boot trouble"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Foxblood on 2007-09-22
Hi, all, I hope you can help me. I had a dual boot machine, Vista and XP. To round it out I installed Ubuntu, using Grub. Now, neither Vista nor XP will boot. I'm not particularly concerned about the XP install, it's the Vista install that I want to be able to use. Vista and XP show in the Grub menu but when I select Vista it seems to start as normal but after the screen with the green progress bar it just goes blank. When this occurred first I decided to use the Vista disc to repair the mbr so I could at least get Vista back. However, the Vista disc won't load normally. It starts the white progress bar to the end and the next screen starts but the repair options don't appear. That's as far as it gets. With fresh installs of XP and Ubuntu I'm prepared to bite the bullet and start from scratch again but if I can't boot from the Vista disc I don't know how to proceed from here. Does anyone know why the Vista disc stops before anything useful appears?
If I have to start again, what's the best way to go about this?

Thanks in advance for any ideas you can offer.

---

### Post by pmoseley on 2007-09-22
Did you alter the Vista/XP partitions when you installed Ubuntu? Shrinking vista NTFS partitions usually cause problems. Shrinking the partition may have corrupted the Vista boot loader and thus vista nor xp will boot correctly.

The vista dvd may freeze on boot because it reads the partition table and sees either 1 or 2 NTFS paritions (depending on your setup) but can't read them properly because of corrupted file system.

---

### Post by Foxblood on 2007-09-22
So, essentially you're saying it's reinstall time?

---

### Post by dfreehill on 2007-09-22
I believe you just need to edit grub and insert lines of text for XP & Vista.
Not sure of the code, but I'm sure you can view the man pages for grub.
If you haven't guessed I'm new here.

---

### Post by Duck2006 on 2007-09-22
This may help

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2)

---

### Post by pmoseley on 2007-09-23
If Vista and XP were on the machine before you installed Ubuntu then the grub-setup should have detected the Vista boot loader and added the correct lines into /boot/grub/menu.lst.

If you tried shrinking a Vista NTFS partition as I did, you probably encountered errors. I'm not 100% on this one but I believe that the 'shrink NTFS volume' is written for XP NTFS volumes, not Vista ones. There are some major differences. My parition became unreadable by the Vista DVD but I managed to use Winternals 5 to recover data and write to another drive before completely reinstalling the system.

If you 'shrunk' a vista partition I'd recommend you reinstall Everything, setting your HDD to allow space for a EXT3 Ubuntu partition and swap space.

Did you actually shrink the partition or am I rambling on about something completely irrelevant?

---

