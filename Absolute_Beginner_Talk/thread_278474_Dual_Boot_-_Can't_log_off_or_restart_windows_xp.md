---
title: "Dual Boot - Can't log off or restart windows xp"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by myounce on 2006-10-16
Installed Ubuntu 6.06 the other day from Live CD.  I'm using Grub as the dual-booter for Ubuntu/WinXP.  I can load either OS just fine when I first boot the PC.  However, when I am in Windows, and try to Restart or log off, the PC hangs.  Windows gets past "Saving your settings..." and dies.  I even have Windows as the default OS in Grub for the sake of the rest of my family who want nothing to do with Linux.

Any ideas on what's cauing this?  It didn't start happening until I installed Linux.

Thanks!

---

### Post by gn2 on 2006-10-16
> **myounce said:**
> Installed Ubuntu 6.06 the other day from Live CD.  I'm using Grub as the dual-booter for Ubuntu/WinXP.  I can load either OS just fine when I first boot the PC.  However, when I am in Windows, and try to Restart or log off, the PC hangs.  Windows gets past "Saving your settings..." and dies.  I even have Windows as the default OS in Grub for the sake of the rest of my family who want nothing to do with Linux.

Any ideas on what's cauing this?  It didn't start happening until I installed Linux.

Thanks!

Can you fit another hard drive?

If so this may help [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by myounce on 2006-10-16
I've only got an old 4 GB secondary IDE in the system - not really ideal.  And I'm not buying a new secondary hard drive just to play with Linux.

Any other ideas?  Is the MBR corrupt?

---

### Post by Irony on 2006-10-16
You can't restart from Windows because that relies on getting to the Windows bootloader via Grub and Grub won't recognise a Windows restart instruction.

You have to shutdown and start.

Perhaps investigate one of the links that shows you how to set up the Windows bootloader to dual boot Ubuntu - I think this involves altering your boot.ini file in Windows.

---

### Post by myounce on 2006-10-16
Thanks.  I'll investigate the Windows bootloader info.

I can't believe I can't find more information on this issue.  It seems like it would be a pretty common problem.

---

### Post by gn2 on 2006-10-16
> **myounce said:**
> Thanks.  I'll investigate the Windows bootloader info.

I can't believe I can't find more information on this issue.  It seems like it would be a pretty common problem.

Lots of Windows info here: [www.theeldergeek.com](www.theeldergeek.com)

---

