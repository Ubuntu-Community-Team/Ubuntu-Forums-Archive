---
title: "Help with Wiping Drive-Windows 98-Ubuntu"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by joshm on 2005-12-31
Hello,
I recently got a really really old laptop from a friend, and I thought I might try installing Ubuntu Linux onto it over the previous version of Windows98 SE. Unfortunetly I realised half way into the install that I didn't have enough space to install Ubuntu, so it forced me to abort the install. I then tried to install Windows 98 by booting into it but it said I didn't have enough space to even install that, which I should be able to as it was already running it before. Does anyone have any command promp scripts or something so I can wipe the C drive? I have tried stuff like "deltree /y c:" or something like that and It never works.
Thanks

---

### Post by coredump on 2005-12-31
If the Ubuntu install was partially done, then your disk may well be in an unstable state.  The partition table may or may not be valid, and the partition(s) may or may not be useable.  If you want to clear the disk out to the state is was in when it was manufactured, you'll need to destroy the partition table.  This will render it unbootable by either Windows or Linux, and you'll have to boot from floppy disk or CD-ROM.  To destroy the partition table from Windows, use 'fdisk' and follow the menus for deleting partitions.  From Linux, the command is also called 'fdisk', but you'll need to supply the name of the disk as well.  This is most likely '/dev/hda'.  So, 'fdisk /dev/hda' will get you into the program and then you can follow the menus, again for deleting partitions.

Once you've destroyed the existing partition(s), you can boot up from CD or floppy disk and install Linux on a completely blank disk.

---

