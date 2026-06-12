---
title: "How to prevent a reinstallation of XP to destroy Ubuntu"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by xcaos on 2008-03-29
Hi,

I need to reinstall XP on my computer. The thing is that I'm afraid that it will over right the MBR thus preventing me from booting into Ubuntu.

Is there a way to prevent this, or do I need to reinstall Ubuntu after XP?

Thanks for the help.

---

### Post by ch_123 on 2008-03-29
You'll need to download a LiveCD called "Super Grub Disk". Follow the instructions and you will be able to install the GRUB MBR after you've installed Windows.

---

### Post by ghost_ryder35 on 2008-03-29
> **xcaos said:**
> Hi,

I need to reinstall XP on my computer. The thing is that I'm afraid that it will over right the MBR thus preventing me from booting into Ubuntu.

Is there a way to prevent this, or do I need to reinstall Ubuntu after XP?

Thanks for the help.

use Virtual Box instead of reinstalling to the hard drive,
or
use the SuperGrub disk and reinstall grub after Windows takes ownership of the MBR (because it will) after the install.

Also make sure to not install over the Ubuntu partitions or you will have to reinstall Ubuntu

---

### Post by mikewhatever on 2008-03-29
When you reinstall XP ubuntu is not destroyed, unless you delete its partition in the process. MBR is the first sector of the HDD and has nothing to do woth Ubuntu or XP. Anyway, it's quite easy to recover grub after you are done with Windows.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub)

---

### Post by arochester on 2008-03-29
See [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by Duck2006 on 2008-03-29
> **mikewhatever said:**
> When you reinstall XP ubuntu is not destroyed, unless you delete its partition in the process. MBR is the first sector of the HDD and has nothing to do woth Ubuntu or XP. Anyway, it's quite easy to recover grub after you are done with Windows.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub)

This is the way to go, try super grub if

[https://help.ubuntu.com/community/Re...ct=RecoverGrub](https://help.ubuntu.com/community/Re...ct=RecoverGrub)

Does not work.

---

### Post by mikewhatever on 2008-03-29
Duck2006, thanks for your advice, but I was only trying to help xcaos and have no problem with GRUB.

---

### Post by Duck2006 on 2008-03-29
> **mikewhatever said:**
> Duck2006, thanks for your advice, but I was only trying to help xcaos and have no problem with GRUB.

No the advice wasn't for you it was for xcaos, sorry if it seemed that way.

---

