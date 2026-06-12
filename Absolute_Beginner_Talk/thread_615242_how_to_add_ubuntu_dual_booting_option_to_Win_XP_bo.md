---
title: "how to add ubuntu dual booting option to Win XP boot loader"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by sandysandy on 2007-11-16
hi guys

i have tried dual booting with win XP with varying success. with grub i am not able to do dual booting. i would be grateful if someone could help me in using the windows XP bootloader to boot ubuntu also.

system specs Pentium D 3.0 GHz, 1GB RAM, 160Hdd SATA hdd ( WinXP - 2 partitions), 40Gb IDE Hdd (Ubuntu 7.10 & Mandriva). Booting sequence is 40GB hdd first.

thanx

---

### Post by Sims2789 on 2007-11-16
[http://highlandsun.com/hyc/linuxboot.html](http://highlandsun.com/hyc/linuxboot.html)

---

### Post by LRT on 2007-11-16
i'm currently dual booting ubuntu 7.10 and windows xp pro. when i first did this it was with ubuntu 7.04 but have since upgraded. i followed every step in this page and it worked perfectly. 

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")

---

### Post by gn2 on 2007-11-16
What order did you install the operating systems?
Did you disconnect each drive when you did so?
Where did you install Grub to?
Have you tried GAG?
Have you read the Hermanzone website? (link in my sig)

---

### Post by sandysandy on 2007-11-16
> **gn2 said:**
> What order did you install the operating systems?
Did you disconnect each drive when you did so?
Where did you install Grub to?
Have you tried GAG?
Have you read the Hermanzone website? (link in my sig)

i have tried installing both ubuntu 7.04 and 7.10 with various options. i have also tried disconnecting each drive, but it did not work.

i have installed grub to hd0 which is the 40 gb hdd having the ubuntu installation.
(installing to hd1 (winxp drive) overwrites mbr and no booting is possible. i have to manually restore mbr with SGD or saved mbr.backup in this case)

i have tried GAG also but was not successful in booting anything but win xp.

thanx

---

### Post by sandysandy on 2007-11-16
> **Sims2789 said:**
> [http://highlandsun.com/hyc/linuxboot.html](http://highlandsun.com/hyc/linuxboot.html)

[QUOTE=LRT]i'm currently dual booting ubuntu 7.10 and windows xp pro. when i first did this it was with ubuntu 7.04 but have since upgraded. i followed every step in this page and it worked perfectly.

[http://www.howtoforge.com/dual_boot_..._ubuntu_feisty](http://www.howtoforge.com/dual_boot_..._ubuntu_feisty)[/QUOTE]

thanx for the links. reading it now

---

### Post by gn2 on 2007-11-17
This might help: [http://ubuntuforums.org/showpost.php?p=1606469&postcount=1](http://ubuntuforums.org/showpost.php?p=1606469&postcount=1)

Check your BIOS boot order to find out which drive is first in the list.

Make the 40gb IDE drive first in the list then add Windows to Grub by a bit of editing, as described by Anaconda and Bulldog.

I would suggest reinstalling Grub to the IDE drive with the Windows drive disconnected, then edit Grub manually.

You may also need to run "fixmbr" on the Windows drive, instructions for that are in Hermanzone.

---

### Post by ronmarley1 on 2007-11-17
> i would be grateful if someone could help me in using the windows XP bootloader to boot ubuntu also.

Previously, when I booted Windows with  my laptop, GRUB got corrupted and and I had to use the SuperGrubDisk to fix.  I think TrendMicro antivirus was the culprit.  I have to use the XP bootloader to boot to GRUB and then into Linux.  The tutorial linked below worked just fine. 
Essentially, create a /boot partition, install GRUB to it, dd the partition to a file called linux.bin, edit boot.ini in Windows, and use the SuperGrubDisk to restore the Windows bootloader.
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html)

---

### Post by jaybombalous on 2007-11-17
I can show u how to do this easy, as long as your bios has an option to boot which ever device on boot-up. Mine is the 'esc' key, u hold it when its finding the drives on boot-up and it will give u a pop-up menu that ask which drive u wanna boot. At this point u select the linux HD to boot too. First u must install linux to this (the second) drive and write grub to the MBR of the drive with linux, NOT windows. Point grub to root (hd0,0).

Easy as that and it works best if u ask me. There is no confusing selections to make and it doesn't over wirte the windows boot loader.

---

