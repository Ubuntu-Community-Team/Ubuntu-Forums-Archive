---
title: "[SOLVED] Install grub from Ubuntnu without reinstalling?"
date: 2008-07-22
forum: Apple Hardware Users
---

### Post by kdb424 on 2008-07-22
I accidentally deleted the boor folder from the linux drive and need to reinstall, but other methods that I look up don't work because it is missing. I have tried everything. any ideas?

---

### Post by cyberdork33 on 2008-07-22
> **kdb424 said:**
> I accidentally deleted the boor folder from the linux drive and need to reinstall, but other methods that I look up don't work because it is missing. I have tried everything. any ideas?
You need a FULL reinstall of GRUB (including files) which is a little different than what is usually covered here.

You should be able to boot the livecd, mount and chroot into your installed system, then reinstall grub with apt-get.

---

### Post by reformedgeek on 2008-07-22
If you deleted the /boot folder, you will have deleted the initrd and vmlinuz files needed to boot on top of the /boot/grub folder.

AFAIK the best option would be to reinstall Ubuntu.  Might be a good idea to put your home folder on a separate partition.  That way you won't have to wipe it when you reinstall the OS.

---

### Post by cyberdork33 on 2008-07-22
> **reformedgeek said:**
> If you deleted the /boot folder, you will have deleted the initrd and vmlinuz files needed to boot on top of the /boot/grub folder.

AFAIK the best option would be to reinstall Ubuntu.  Might be a good idea to put your home folder on a separate partition.  That way you won't have to wipe it when you reinstall the OS.
Oh, yep, I didn't see that you deleted the whole boot folder... reinstall time.

---

### Post by kdb424 on 2008-07-22
Did that. I ended up triple booting. lol Thanks for the help!

---

### Post by cyberdork33 on 2008-07-23
Please mark as solved (Thread Tools menu)

---

