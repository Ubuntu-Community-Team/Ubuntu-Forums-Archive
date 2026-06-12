---
title: "Need help putting Windows on Feisty desktop"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Jump on 2007-04-29
I tried this back during the Hoary days but it was recommended to load Windows first then Ubuntu. This worked for me with very little hassle. It's also allowed me to put xp, vista and feisty on a new laptop.

My question is for a friend who recently allowed me to install feisty on desktop. He's a completely new to linux so I did all the setup with beryl, dual monitors, his logitech mouse and keyboard, etc. The problem is now he wants to add windows back as a dual boot so he can plays certain games. I'm wondering whether I can install XP on a new partition and then update grub to boot from both OS. Is this possible or does Windows for some reason insist on being the first partition? I seem to recall that being the problem I had back when I used Hoary.

---

### Post by psionyk on 2007-04-29
My understanding is that yes, Windows needs to be on the first partition of the drive, and it also needs to be flagged as bootable.  The problem with reinstalling Win after Ubuntu, is that Windows has an automatic (and nasty) result of overwriting the MBR, which means that GRUB will be deleted, and you will not have a menu to choose to boot into Ubuntu.  First off, ask him what games he is looking to play in Windows, as there may be compatibility for those games in WINE:

[[COLOR="DarkRed"]_http://appdb.winehq.org/_[/COLOR]]("http://appdb.winehq.org/")

If he still wanted to use Windows, you would either have to wipe the hard drive and start from scratch, installing Windows on part of the drive first, followed by Ubuntu which would install GRUB properly and detect/boot both OS's; or you would have to shrink the Ubuntu partition making room at the start of the disk, installing Windows into that space, and then reinstall GRUB into the MBR using something like Super GRUB disk:

[[COLOR="#8b0000"]_http://supergrub.forjamari.linex.org/?section=features_[/COLOR]]("http://supergrub.forjamari.linex.org/?section=features")

Just depends on how much has already been set up in Ubuntu, and whether you're willing to reset it for him.

---

### Post by randell6564 on 2007-04-29
All you have to do is reinstall grub after the Windows install.  [This]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_restore_GRUB_menu_after_Windows_installation") will show you how.

Cheers!

---

