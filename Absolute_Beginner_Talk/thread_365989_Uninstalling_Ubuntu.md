---
title: "Uninstalling Ubuntu"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Mueez on 2007-02-20
hi guys,

I want some help on how to uninstall Ubuntu...

I tried formating the drive but this gives me error regarding "GRUB"...
What should i do to uninstall both "GRUB" and Ubuntu?????Please Help!

---

### Post by jml on 2007-02-20
Since Grub is usually installed in the master boot record, a standard format will not remove it.  In practical terms one does not need to remove a Linux distribution, one simply installs over it.  If you were dual booting with Windows and you want to go back to just windows, then you just boot with your Windows install CD, or your System restore CD depending on what you have.  As you boot, you should be offered a chance to repair the boot record.  I don't remember the details, but once you let Windows repair the boot record, it will overwrite the Grub boot loader and you should be good to go.  If you simply want to remove it so you can install a different Linux distro, then simply boot that distro's install CD and the installation process will remove all traces of the earlier install.

Joe

---

### Post by Aberrix on 2007-02-20
If you have an old win98 boot disk you can do a ```
fdisk /mbr
``` to format the Master Book Record.

---

### Post by oceanspray on 2007-02-20
> **jml said:**
> Since Grub is usually installed in the master boot record, a standard format will not remove it.  In practical terms one does not need to remove a Linux distribution, one simply installs over it.  If you were dual booting with Windows and you want to go back to just windows, then you just boot with your Windows install CD, or your System restore CD depending on what you have.  As you boot, you should be offered a chance to repair the boot record.  I don't remember the details, but once you let Windows repair the boot record, it will overwrite the Grub boot loader and you should be good to go.  If you simply want to remove it so you can install a different Linux distro, then simply boot that distro's install CD and the installation process will remove all traces of the earlier install.

Joe

Would add to this that when you get to the Repair section type this at the prompt: "fixmbr" ...type "Y" and "Exit" and you're good to go.

Good Luck

---

### Post by tyk on 2007-02-24
even after installing grub into the mbr? fixmbr said it could destroy partition tables.. eeps.. even now grub loads but has trouble differentiating between the two HDs. in device.map it's correct but grub recognizes the windows installation only after being told to flip hd mapping .. it doesn't recognize the ubuntu installation at all while any installation cd does (win/lin). change in menu.lst or device.map changes nothing..
is fdisk /mbr the only way to restore mbr? can ntldr load ubuntu/linux? should i be posting this in a grub forum :) 
eventually i dont want linux on this machine, rather a fat32 partition and a win workstation.

---

