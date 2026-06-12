---
title: "Problems restoring system"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by tech9 on 2007-09-17
After running this command "tar xvpfz backup.tgz -C /" under root profile - I reboot the system and am encountering this error...

/bin/sh: can't access tty; job control turned off
(initramfs)

Anybody have any idea why my restore failed?

Thanks!

---

### Post by tech9 on 2007-09-17
no one huh? :(

---

### Post by mannheim on 2007-09-17
Between making the backup and doing the restore, did you have to reformat any partitions? Also, is the restored system on the same partition as the old one?

One possible cause of this sort of failure is that the system fails to find the correct root filesystem during boot. This can be because of something wrong in the grub configuration file /boot/grub/menu.lst, or in the file /etc/fstab.

See, for example, [this post.]("http://ubuntuforums.org/showpost.php?p=2571293&postcount=288")

---

### Post by tech9 on 2007-09-17
> **mannheim said:**
> Between making the backup and doing the restore, did you have to reformat any partitions? Also, is the restored system on the same partition as the old one?

One possible cause of this sort of failure is that the system fails to find the correct root filesystem during boot. This can be because of something wrong in the grub configuration file /boot/grub/menu.lst, or in the file /etc/fstab.

See, for example, [this post.]("http://ubuntuforums.org/showpost.php?p=2571293&postcount=288")

mannheim,

Thank you for being the only one to respond to my question! It looks like I stumped everyone else with this. I ended up rebuilding from scratch. I already had my data backed up to a tar file.

Take Care,

T9

---

