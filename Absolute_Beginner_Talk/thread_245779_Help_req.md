---
title: "Help req"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by thedivvyman on 2006-08-28
Hi - heres the story.
Started with  a SATA drive with XP installed on it - no problem.
I then installed another SATA drive after disconnecting the first, so I could do a dual install of XP and Ubuntu without risk to the contents on first drive. May I add here that both installs were totally successful and the GRUB boot thingy worked offering  to boot XP or Ubuntu.
You're gonna laugh now - cos I just tried reconnecting my original SATA drive to get some info (addresses) and according to the first screen (splash) I have zero  drives installed. It sees my two cd roms and the floppy but no HDD. Any help on this would be much appreciated.
Thanks

---

### Post by Metacarpal on 2006-08-28
Here's what I recommend:

Put both drives back in, mark the XP drive as the first boot device in your BIOS.

Reinstall Ubuntu from the CD without disconnecting either drive.

When you get to the partition manager, just don't tell it to format both drives and you'll be fine.  Ubuntu will detect your Windows install and dance around it.  You shouldn't lose a thing unless you tell the installer to re-partition your Windows drive.

Edit: Um.  Obviously, if the Windows HDD is listed as your first boot device, you can't boot from CD.  I'm kind of slow today. 8-[

---

