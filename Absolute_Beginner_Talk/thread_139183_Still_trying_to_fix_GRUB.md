---
title: "Still trying to fix GRUB"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-03-03
I tried to follow Arnieboy's [wiki]("http://www.ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub"), but when I try to continue after manually editing the partitions (without formatting) I receive the following message:

*No root file system is defined* 

Is there any other option, or am I forced to re-install?

(BTW The only OS that will boot now is XP - FreeBSD & Ubuntu won't boot when selected on BSD's bootloader.)

---

### Post by angkor on 2006-03-03
[http://www.ubuntuforums.org/showthread.php?t=52505&highlight=grub-install+%2Fusr](http://www.ubuntuforums.org/showthread.php?t=52505&highlight=grub-install+%2Fusr)

This thread has a couple of options.

---

### Post by Cousindaddy on 2006-03-03
Yes, I've tried all of those things...  I get error messages saying something about "stage1."  I'll keep bumping this for awhile...and see if anybody has anything new...otherwise I think I'll have to do a FixMBR from XP and go from there...
Thanks for the reply though...

---

### Post by LordBug on 2006-03-03
It sounds like Grub may not be installed and/or configured correctly.

Can you provide output of "sudo fdisk -l" and "sudo cat /boot/grub/grub.conf"?

---

### Post by Cousindaddy on 2006-03-03
Can I do those commands from the Live CD?

---

### Post by Cousindaddy on 2006-03-03
Appologies...I answered my own question.  Here is the output for *sudo fdisk -l*:

> Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        7140    36869175    f  W95 Ext'd (LBA)
/dev/hda3   *        7141       11190    32531625   83  Linux
/dev/hda4           11191       14946    30170070   a5  FreeBSD
/dev/hda5            2551        5651    24908751    7  HPFS/NTFS
/dev/hda6            6965        7140     1413688+  82  Linux swap / Solaris


The command *sudo cat /boot/grub/grub.conf* returns: 
*cat: /boot/grub/grub.conf: No such file or directory*

---

### Post by Cousindaddy on 2006-03-03
bump

---

### Post by Storm Rider on 2006-03-03
Hello,

Which file systems are you using on the various OS's?  What I've found is that Fedora Core with it's default Ext3 file system and a root partion (mount point) labelled as "/" screws up Suse's ReiserFS and Ubuntu's Ext3.  Sounds to me like you've got similar problems.

Is Ubuntu's , Grub the one diplayed when you boot up?  If it isn't, I'd reinstall Grub;)

---

### Post by Cousindaddy on 2006-03-03
I'm using XP and FreeBSD... 

My problem has been that I cannot re-install or repair GRUB - regardless of whichever tutorial I follow.

XP and BSD seem to boot okay...although BSD is giving me some wireless keyboard and mouse issues to sort through...

I think it must be a lost cause.

Darn, I had my desktop and browser tweaked nicely too...oh well...at least no one was hurt...

Thanks for the reply.

---

