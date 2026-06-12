---
title: "Feisty Fawn install - No Grub?"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by rorschach on 2007-03-28
I am trying to install Feisty Fawn (after removing the splash --, since I have an ATI card ;-)). The install seems to go well, up to the point where I am told by the installer to reboot to enter the newly installed environment.

However - nothing happens. Windows XP comes up, with no Grub selection screen (I am setting up a dual boot system).

Any idea why grub might not be installing... or how I can set it up myself?

---

### Post by hyper_ch on 2007-03-28
Hmmm, do you have two harddisks and one is IDE and the other one is SATA?

That was the situation where I had problems with the installation of feisty fawn.

---

### Post by rorschach on 2007-03-28
I have only SATA drives.

---

### Post by drs305 on 2007-03-28
> **hyper_ch said:**
> Hmmm, do you have two harddisks and one is IDE and the other one is SATA?

That was the situation where I had problems with the installation of feisty fawn.

Can you elaborate and provide a recap of your solution? I'll have the same setup. Thanks.

---

### Post by hyper_ch on 2007-03-28
Well, my problem was using IDE and SATA drives that grub was installed in the sata mbr however my bios was first trying to boot from the ide drive. I had to set it the sata drive. But since yours is all sata I can't really help you there.

---

### Post by rorschach on 2007-03-28
More info on my problem:
I have gone in and double-checked my grub install by trying sudo grub

The only problem I can see in the setup is this:
when I reboot from the LiveCD supposedly into the newly set-up feisty fawn install - when the system stops to eject the cd, it states to hit enter to continue - when I hit enter, I only get ^M displayed.
I try hitting ctrl-alt-del, and I get a notice that the system is going down in 30 seconds.
a few minutes later, I finally resort to hitting the hard reset button on my computer, and I boot directly into windows - again, no grub bootloader.

Any help?

---

### Post by rikai on 2007-04-02
Tried changing the boot order of your hard drives in your bios?
It could be that your grub is installed tot he MBR on the other drive, and as suchdoesnt have a chance to load because it sees your windows mbr first.

---

### Post by irw on 2007-04-03
I have had problems with grub, but at a slightly earlier point.

Laptop, 2 sata drives.  Already running XP (soon to be removed totally) and Edgy.  I boot into edgy via the windows boot loader because I kept getting grub error messages when first installed

installing Feisty, it gets to the point of installing GRUB on hd0, then stops, complaining it cannot install grub and this is a fatal error.  This is the same with the live CD, or the alternate install CD.


Any ideas, anyone?

---

### Post by juanhunglow on 2007-04-03
> **rorschach said:**
> I am trying to install Feisty Fawn (after removing the splash --, since I have an ATI card ;-)). The install seems to go well, up to the point where I am told by the installer to reboot to enter the newly installed environment.

However - nothing happens. Windows XP comes up, with no Grub selection screen (I am setting up a dual boot system).

Any idea why grub might not be installing... or how I can set it up myself?


Have you found any more information on this problem?  

I started another [_**thread **_]("http://www.ubuntuforums.org/showthread.php?t=400015")for my problem which is slightly different b/c I'm not dual booting, but, after a fresh install of anything, edgy, dapper, feisty, I get no grub.  I can only boot into the installed OS by using the live CD and telling it to "boot from first HD"
Grub is not working.
This problem wouldn't be so irritating if it had happened in the past, however, prior to this attempted install of feisty, any version of ubuntu I used up to this point didn't have any problems booting.  I'm fearful that I might have some hardware problem now.

---

