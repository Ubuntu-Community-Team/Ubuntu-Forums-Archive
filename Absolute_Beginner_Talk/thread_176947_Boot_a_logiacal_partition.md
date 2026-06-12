---
title: "Boot a logiacal partition?"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2006-05-15
I want to triple boot MS, FC5 and, Brezzy.  If I install MS on hda1, FC5 on hda2, swap on hda3 can I make a extended partition and install brezzy on hda5?  Will it be able to boot if I install grub from brezzy on hda1?  Thanks,  I am just learning about extended and logical partitioning.

---

### Post by Jose Catre-Vandis on 2006-05-15
Yes, this should work fine. Linux/Dapper is happy running from a logical partition.

---

### Post by echo $USER on 2006-05-15
can i just put the swap partition on a logical partition?

---

### Post by catlett on 2006-05-15
You can start with all logical aprtitions. The installer will make it what it wants. You will have to "manually edit" the partition table and choose those partitions seperately. Each time you choose one you have to go through a set up of what kind of filesystem, what to mount it as and where it's mount point is.
Before you install breezy make a copy of your FC5 /boot/grub/menu.list. FC5 didn't acknowledge my Ubuntu install and Ubuntu didn't acknowledge my FC5 install when I didi it the other way around.
If you have a copy of your grub menu from fc5 then all you have to do if Breezy doesn't recognise it is copy the FC5 entry into your Ubuntu grub list.
If you know that FC5 is going to be on hda3 you can also manually enter it into grub during install. Grub will ask you if there are other OSs it doesn't recognise (if it doesn't list fc5) answer yes. Click on add. It will ask you to enter a name. Enter FC5. It will ask where it is. Enter /dev/hda3. Then grub will enter a chainloader listing like it does for windows pointing at hda3.
It's not as complicated as it sounds. If entering it during install doesn't work you can always edit the menu list. Good luck.

---

