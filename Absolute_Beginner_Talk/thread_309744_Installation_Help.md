---
title: "Installation Help"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by debbi8 on 2006-11-30
Hi, all - I had been playing with the new Ubuntu 6.10 live cd and decided that I liked it so much I would install it onto a maxtor 300Gb ext usb hdd (My first, stumbling tentative steps towards freedom from M$ tyranny!:D ).  For some reason I just couldn't get it to work, so I took the hdd out of the case and installed it in my HB system (p43.06HT, Asus P4G8X MB, (2)Seagate 120Gb SATA HD in raid 0 with WXPPSP2, 1GB ram, Nvidia 6600GT, Sony DVD/CD, Hauppauge 250 TV card) with an IDE cable to the primary slot (no jumper).  I then went in through the live cd and partitioned 5Gb for the root, 1.024Gb for the swap files, 44 Gb for all else linux, and a nice big fat 250GB ntfs partition for WXP media files. Grub was set to load onto the hd0.  Installation seemed to complete w/o any problems, but when I boot up Ubuntu (which I can only do after changing the boot sequence in my bios) Grub initializes, the Ubuntu splash screen starts, then just freezes.  No error codes or anything.  Once I change the boot sequence back, I can boot to WXP w/o problems and can see the 250GB space as an extra drive under my computer.  Am I doing something wrong or missing something ](*,)?  Thanks!

---

### Post by Ecthelion on 2006-12-01
My advice is that you try to boot again without the quiet option.
When in grub, push the button to edit the boot menu's.
Delete all the "quiet" that you find (two times usually), and try to boot it up. When booting up try Ctrl-Alt-F1. And tell us what the error message is you (should) see on your screen.

If this doesn't work because it freezes before you can do anything, then I would recommend you to do check your cd (it's an option when you have to choose to start up with live cd), and if the cd is ok, reinstall Ubuntu.

(Probably the second option will be easier anyway...)

---

