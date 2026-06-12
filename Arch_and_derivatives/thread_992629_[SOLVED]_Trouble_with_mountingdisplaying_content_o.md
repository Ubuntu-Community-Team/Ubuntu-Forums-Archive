---
title: "[SOLVED] Trouble with mounting/displaying content of external HDD"
date: 2008-11-24
forum: Arch and derivatives
---

### Post by Dani Filth on 2008-11-24
Hello folks,

I've been using Arch for a few months (nearly a year) and I've been able to deal with most of the common issues so far. But only one still remains troubling me, whenever I try to plug in the external HDD and display its content, I get the message "Permission denied" or "You don't have permission to access" or something like that (sorry, I'm currently not at home so I don't have the external HDD to get the exact message).

In addition, the weird thing is, thumbdrives (with disksizes are 1GB, 2GB, 4GB) work just fine, the computer is able to detect the thumbdrive, its name/label, and display the content nicely. 
But when it comes to large capacity external HDD (I have 2 of them : 80GB & 500GB), the computer is able to detect the HDD & its name but it fails to display the content, and I cannot copy anything from/to the external HDD.

For your information, I did add my user to group "storage", I also set "chown, chgrp, chroot" as needed. I mount the external HDDs/thumbdrives to /mnt/hd_ext.

Does anyone have experience with this before, please help me to solve this.
Much appreciated for your helps :D

---

### Post by kpkeerthi on 2008-11-25
How are you mounting the drives? Using FSTAB? or automounting via HAL? What is filesystem type of the drive?

---

### Post by mips on 2008-11-25
Are you using the same username as you did previously (before Arch) to access the drive?

---

### Post by Dani Filth on 2008-11-25
> How are you mounting the drives? Using FSTAB? or automounting via HAL? What is filesystem type of the drive?
I'm not much of an experienced user so I don't know how to use/deal with fstab, I think it is automounted via HAL then - sorry about this, I'm not entirely sure - the HDD's icon appears on the desktop and in Thunar, so I guess it's automatically mounted by HAL? The file system on the drives is NTFS because sometimes I need to copy from other friends who use 'doze.

> Are you using the same username as you did previously (before Arch) to access the drive?
I only have 2 accounts on my computer, the user account and root account. And I only use root when it's required, so the user account is the same.
EDIT: Err, I'm not sure what you mean by "before Arch", when I installed Arch, I chose to format & destroy everything on the harddisk entirely, though.
And just in case it's needed, I'm using Arch+XFCE.

Cheers!

---

### Post by kpkeerthi on 2008-11-25
> **Dani Filth said:**
> 
 I also set "chown, chgrp, chroot" as needed. I mount the external HDDs/thumbdrives to /mnt/hd_ext.
D
You cannot use chown to change permission in NTFS volumes as NTFS does not support Linux/Unix permissions.

You may add an FSTAB entry with uid, gid, dmask mount options so you, as a user (non-root), can access it without sudo/gksudo/su.

See [http://wiki.archlinux.org/index.php/NTFS_Write_Support](http://wiki.archlinux.org/index.php/NTFS_Write_Support) for manual mount using FSTAB

See [http://wiki.archlinux.org/index.php/HAL](http://wiki.archlinux.org/index.php/HAL) for automount using HAL. Has instruction for mounting NTFS with specific dmask mount options

---

### Post by kpkeerthi on 2008-11-25
--bad post--

---

