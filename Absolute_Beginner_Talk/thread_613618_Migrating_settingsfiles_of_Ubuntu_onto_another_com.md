---
title: "Migrating settings/files of Ubuntu onto another comp"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by Kingfield on 2007-11-15
Is there any way to do this? And i mean migrating all settings of ubuntu onto another computer? (Also Ubuntu). Also if this is possible, is it also possible between different VERSIONS of Ubuntu?

Thanks in Advance.

---

### Post by CatKiller on 2007-11-15
It's probably worth installing Ubuntu each time if the hardware is different so that any hardware-detection scripts can be run.

User settings are kept in the Home folder, so after you've created the users you can just copy their home folders to /home on the new computer and all of the users will have their settings still.

Installed programs are cached in /var/cache/apt, if you didn't want to download the files again. Just copy those over and install the programs on your new computer.

Or, if you're feeling brave, you can just copy everything to the hard drive in the new computer, and then edit the /etc/fstab, /boot/grub/menu.lst and /etc/X11/xorg.conf to refer to the new hardware.

---

### Post by Kingfield on 2007-11-16
Ahh that's all i needed to know, thanks alot!

---

### Post by Kingfield on 2007-11-17
> **CatKiller said:**
> It's probably worth installing Ubuntu each time if the hardware is different so that any hardware-detection scripts can be run.

User settings are kept in the Home folder, so after you've created the users you can just copy their home folders to /home on the new computer and all of the users will have their settings still.

Installed programs are cached in /var/cache/apt, if you didn't want to download the files again. Just copy those over and install the programs on your new computer.

Or, if you're feeling brave, you can just copy everything to the hard drive in the new computer, and then edit the /etc/fstab, /boot/grub/menu.lst and /etc/X11/xorg.conf to refer to the new hardware.

On second thoughts, are you sure the installed programs are placed there? Because ona quick scan through there are only bout 20 debs there, and i cant find aMSN or any of the programs that i use other than the pre-installed ones.

---

### Post by CatKiller on 2007-11-17
They aren't installed there - files get put all over the place when programs are installed - by they are downloaded to there to install from if you use Synaptic, apt-get or aptitude. You'd still need to use one of those to install the programs with, but they should be installed from the .debs rather than downloading them again.

Possibly something else has cleaned your cache.

---

