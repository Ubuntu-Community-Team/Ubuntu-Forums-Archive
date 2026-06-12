---
title: "Booting Trouble!!"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by vipin on 2006-02-10
What is the way to modify the boot sector of a Hard disk ? 

Like suppose I install Windows XP on my computer, it makes the hard disk bootable by modifying its disk space. Now, suppose I decide to install Ubuntu on my computer too and have a dual boot of Windows XP and Ubuntu(5.04i).  Since Ubuntu requires partitioning of harddisk, I decide to install it on a separate hard disk. During installation, it says to install GRUB BOOT LOADER to my first harddisk or gives option to install to a floppy. I decide to install on my first hard disk. Now, my computer is bootable only if my ubuntu harddisk is connected, and I cannot boot from my main hard disk if I remove my ubuntu harddisk. Now what to do in such a situation? Say suppose, my ubuntu harddisk was old and now it has crashed, how can I make my computer bootable back to Windows XP again? I think installing Windows XP again from its CD will do the job but I am not sure. And what to do if I cannot reinstall Windows XP or if I don't have its CD?

 Is there any way to modify or rollback the boot sector of my first harddisk?

---

### Post by Packard Dell on 2006-02-10
check this out on how can you fix your MBR without re-installing your WinXp all over again: [http://www.ubuntuforums.org/showthread.php?t=126082]("http://www.ubuntuforums.org/showthread.php?t=126082") (look out for the **FIXMBR** procedure). you can actually install GRUB on a floppy disk if you like so that you won't have to worry all about this.

---

