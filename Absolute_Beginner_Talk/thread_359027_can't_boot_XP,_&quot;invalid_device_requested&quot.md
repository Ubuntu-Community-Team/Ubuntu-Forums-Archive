---
title: "can't boot XP, &quot;invalid device requested&quot;"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by mdknaebel on 2007-02-11
I recently installed Ubuntu 6.10 on a computer on which I also run Windows XP Pro.  I made sure not to delete the XP partition, and the XP folder is seen on my desktop of Ubuntu and I can look through it,  However, In GRUB, I added the choice of Windows XP, based on my boot table and the help of others.
When I select the XP choice in GRUB at boot, it says:  "Error 12: Invalid device requested"

My boot table:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 1 1530 12289693+ 83 Linux
/dev/hda2 1531 9732 65882565 f W95 Ext'd (LBA)
/dev/hda5 1531 9732 65882533+ 7 HPFS/NTFS
Edit/Delete Message 

I have tried hd0,1 and hd0,4 as the root when editing, and got the same error both times.

Here is a link to the other thread: [http://ubuntuforums.org/showthread.php?t=358502]("http://ubuntuforums.org/showthread.php?t=358502")


Any Ideas?

Thanks!

---

### Post by tbroderick on 2007-02-11
Can you post your grub /boot/grub/menu.lst?

---

