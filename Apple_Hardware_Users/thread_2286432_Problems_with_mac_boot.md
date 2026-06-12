---
title: "Problems with mac boot"
date: 2015-07-12
forum: Apple Hardware Users
---

### Post by joe175 on 2015-07-12
First post time

So I new to linux, but I have used it in virtual machines and stuff like that and I finally wanted a dedicated computer. So I have an older 2008 macbook pro that has been collecting dust, so I decided to install linux on it. I installed ubuntu on a bootable disk and completely replaced mac OSX with ubuntu. I did this without realizing that mac is EFI based, not BIOS. Now ubuntu doesn't boot from the power on, but everything is partitioned correctly. I can access the files via using the bootable disk as a 'preview' for linux.  Although it runs from the disk drive, it gives me full access to the internal drive and files. 

So, is there anything I can do to have it boot correctly, or am I screwed? Keep in mind, I no longer have access to mac OSX. Also, after inserting the disk, it gives me BOTH options to using EFI boot (Linux install disk) or windows (blank).

Thanks guys!

Edit: Quick update, I was about to make an EFI boot partition, and it shows in the bootable options, but whenever it tries to boot, it freezes the computer.

---

### Post by QIII on 2015-07-12
Moved to Apple Hardware Users.

---

### Post by este.el.paz on 2015-07-14
You're "screwed," man . . . .  Personally I would say to wipe the disk and re-install OSX in one partition, then install rEFInd using OSX Terminal following his instructions on how to do that.  Then use Disk Utility to set up the amount of space you want for linux, formatted as "free space" or "fat32" . . . then go back to the linux install disk and try the "automatic" "install alongside OSX" option . . . and see how that goes.

You ***may*** be able to install rEFInd using the linux terminal, following "rodbooks" instructions to do that . . . or, you might try "SuperGrub2" CD to see if you use it to boot the linux system and then get into "repair GRUB" and see if that fixes your install.  General wisdom seems to be to keep a minimal OSX partition on an apple.  Others might post here giving you instruction on how to have an OSX-free system . . . doesn't take too long to "nuke n pave."

e..

---

