---
title: "[solved] GRUB overwrote MBR making drive unbootable"
date: 2009-03-05
forum: Apple Hardware Users
---

### Post by IdentifyTarget on 2009-03-05
I'm posting this information in hopes of saving other people time in the future. I rebooted my system using Ubuntu 8.10 LiveCD. I installed ubuntu onto an external drive and promptly reboot my system expecting to be able to choose between the external drive and my Mac OS X drive. Unfortunately I made a mistake during the install. I accidentally installed the bootloader. This caused my mac to not recognize my hard drive.

After some research I discovered this solution.

[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

rEFIt, is an EFI repair/maintenance program.  I burned a bootable CD and selected GPT Sync. That updated my old MBR code. This made my drive bootable.

I was able to fully recover the drive doing this. Hope this helps someone.

---

### Post by cyberdork33 on 2009-03-05
> **IdentifyTarget said:**
> I'm posting this information in hopes of saving other people time in the future. I rebooted my system using Ubuntu 8.10 LiveCD. I installed ubuntu onto an external drive and promptly reboot my system expecting to be able to choose between the external drive and my Mac OS X drive. Unfortunately I made a mistake during the install. I accidentally installed the bootloader. This caused my mac to not recognize my hard drive.

After some research I discovered this solution.

[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

rEFIt, is an EFI repair/maintenance program.  I burned a bootable CD and selected GPT Sync. That updated my old MBR code. This made my drive bootable.

I was able to fully recover the drive doing this. Hope this helps someone.
This is well documented in installation wiki. It occurs even when you don't install grub to the MBR.

P.S. If you'd like to boot from an external, it won't work without some extras. See:
[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

---

