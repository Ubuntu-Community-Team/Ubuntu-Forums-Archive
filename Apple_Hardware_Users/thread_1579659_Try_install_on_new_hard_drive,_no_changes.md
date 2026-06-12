---
title: "Try install on new hard drive, no changes?"
date: 2010-09-22
forum: Apple Hardware Users
---

### Post by Northern Mike on 2010-09-22
I don't know anything about EFI and reading here worried me. [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
 
I want to do a full install to a new hard drive, Ubuntu only, and if the guy does not like it swap back to the old hard drive with OSX as if nothing happened. Nothing will be changed?
 
It's a Macbook 1.1, helping a friend upgrade the ram on it and he wants to try Ubuntu. I don't want to try if it will make any changes to the EFI bios thing and he can't swap his old drive back in. Sorry if this is a silly question but I know nothing about Macs.

---

### Post by grahammechanical on 2010-09-22
It is like the man on the game show said: the questions are easy if you know the answers. Your question is not a silly question.

When the computer boots it will look for an Operating System. Depending on the settings in the BIOS it will look for an OS on a floppy drive or a CD/DVD drive or a hard drive. The order can be changed. If boot from CD comes before boot from HD then a Ubuntu live CD will work. If you exit the live Cd then on re-boot the computer will boot the OS on the hard drive. Is this not true?

When I built my computer a couple of years ago I first tested it out using a floppy drive with DOS on it. Then I tried out the Ubuntu live CD. Then I installed Ubuntu.

If you replace the HD with Ubuntu installed with the HD that has OSX on it, then OSX will load. After all you are not changing anything on the HD. It is possible to install both hard discs and use Grub to select which OS to boot from. One HD needs to be set as Master, the other as Slave. There should be little pins at the backs of the drive that you can change. Of course I may be out of date with this information. But I think that you can do what you want.

Regards

---

### Post by Northern Mike on 2010-09-22
Will EFI remain unchanged though?   That link was a little unclear and I don't want to brick a friends system.  I've built a handful of systems and am aware what happens if a bios flash goes wrong.  The mod stepping mid write up and suggesting against following anything but a dual boot made me wonder if you were somehow making an irreversible change to the bios (EFI).   I think he means it only makes changes to the drive you are installing to but I want to make sure.   Everyone knows once you help someone with an install or an upgrade you pretty much own every problem that computer will ever have.  I just want to make sure I'm not creating work for myself before I start.

---

