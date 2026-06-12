---
title: "Need Linux Install HELP!"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Noobuntu61 on 2007-08-21
hey guys just a real quickie does dual booting linux affect another os like say vista? because the last thing i want is to install linux and need to remove it for any reason only to find that my computer is negatively affected.

---

### Post by WanderingKnight on 2007-08-21
Dual booting works perfect with Linux. Just be sure NOT to install Windows after Linux, because the Windows bootloader isn't Linux friendly.

---

### Post by Ek0nomik on 2007-08-21
You can dual boot both Vista and Ubuntu.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

[http://ubuntuforums.org/showthread.php?t=207870](http://ubuntuforums.org/showthread.php?t=207870)

[http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot](http://www.eloff.se/tutorials.php?ubuntu_vista_dualboot)

You will probably want a fresh install of Vista first so the files aren't scattered across the hard drive.

---

### Post by benerivo on 2007-08-21
Yes, it needs to take control of what OS boots, so it will delete the Vista loader and replace it with a loader that points to both Ubuntu and Vista OS's. I wouldn't be worried about losing your system if you are able to reinstall Vista (ie. you have the rescue CD or similar).

---

### Post by Noobuntu61 on 2007-08-21
Thanks again guys but do i have to reformat the hard drive because even though i have backed up my data i still don't want to lose anything.

---

### Post by MQMike on 2007-08-21
Vista   ***   The definitive dual-booting guide: Linux, Vista and XP step-by-step
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

That's the one to see.
There are some issues (shrinking partitions, etc.) but it's all doable and safe.
The apm guide will alert you to these issues and how to handle them.


GRUB stuff:
Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

If you do need partitioning/formatting get GParted Live CD:
GParted:   [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
GParted how-to:   [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Ek0nomik on 2007-08-21
> **Noobuntu61 said:**
> Thanks again guys but do i have to reformat the hard drive because even though i have backed up my data i still don't want to lose anything.

If you have been running Windows rather actively for more than a few days you will want to reformat because if you don't you will be losing data anyway.  Unless you can defragment the hard drive and take care of the scattering.

---

