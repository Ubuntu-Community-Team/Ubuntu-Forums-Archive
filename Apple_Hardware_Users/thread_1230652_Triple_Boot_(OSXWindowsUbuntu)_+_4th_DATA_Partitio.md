---
title: "Triple Boot (OSX/Windows/Ubuntu) + 4th DATA Partition?"
date: 2009-08-03
forum: Apple Hardware Users
---

### Post by vostok4 on 2009-08-03
Is it possible to have a triple boot system, OSX, Win7 and Ubuntu (say 50GB for each OS partition) and then the rest of the harddrive space as a DATA partition (NTFS for example) that can be shared between Win7 and Ubuntu, as a GPT partitioned disk?

Does anyone have any insight on how to go about this? I've been reading about nuking the EFI partition, but I was hoping to use rEFIt as the menu to boot the different OSes...

---

### Post by quixote on 2009-08-04
rEFIt, I gather, loads first, allows you to choose between OSX & everything else.  Then grub would be the next level and allow you to choose between the other OSes.  Don't nuke the EFI partition until you're sure that's what you want to do.  

Have you already seen the [ubuntu Apple Intel Installation]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation") wiki?  Towards the very end is a bit on OSX / Vista / Ubuntu install.  Since Vista is Win7 - service pack 1 ;) I'd think those instructions would apply.  One issue is that Windows is fussier about playing nice with other OSes, so there may be issues with the order in which they need to be installed.  Not sure if that's still true with Win7, but I'm sure they discuss it on the wiki page.

The fourth data partition is no problem.  You could have as many data partitions as you liked. Of course, you can only have four primary partitions, so you'll need an extended partition to contain logical partitions.

---

