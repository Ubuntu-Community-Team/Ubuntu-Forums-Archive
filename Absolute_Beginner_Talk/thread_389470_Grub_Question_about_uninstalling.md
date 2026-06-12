---
title: "Grub Question about uninstalling"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by rennen01 on 2007-03-20
If I completely uninstall all the Linux Distros on this PC and leave the Windows XP alone, is the XP still usable?

I want to completely wipe all the Linux Distros out and start over with fresh installs.

Should I be able to boot into XP directly after me uninstalling everything?

---

### Post by Tomosaur on 2007-03-20
> **rennen01 said:**
> If I completely uninstall all the Linux Distros on this PC and leave the Windows XP alone, is the XP still usable?

I want to completely wipe all the Linux Distros out and start over with fresh installs.

Should I be able to boot into XP directly after me uninstalling everything?

If you remove every Linux partition, then you may not be able to boot into Windows, depending on your current bootloader. Grub certainly won't work. If you have your XP recovery disk to hand, then you need to run that and use the 'fixmbr' command at the recovery console. This will reset the MBR to the windows MBR.

If you remove all of the Linux installs, then reinstall Linux before trying to boot into Windows, then you should be fine.

Either way - your Windows installation won't be damaged, it will just be that bootloader on the MBR won't work properly without a Linux install (because the boot configuration files are installed in the Linux boot directory). You don't need to worry about 'breaking' Windows - but you WILL need to reconfigure your MBR to either the Windows MBR (which will only boot Windows) or a different standalone bootloader, such as GAG, which will allow you to select which OS you want to boot from without relying on any files on your hard drive. As long as you have a floppy drive, you can use GAG.

Alternatively, you can boot into Windows right now, and find and install the 'Grub for Windows' program, which will mean GRUB will work after you remove Linux.

---

### Post by rennen01 on 2007-03-20
Thank you very much :)

---

### Post by rennen01 on 2007-03-20
It worked! Now I can use Live CDs again.  Funny thing is it wouldn't work until I reformatted the swap partition. :confused:

---

