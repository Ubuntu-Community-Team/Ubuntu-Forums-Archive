---
title: "Move from boot partition to boot folder"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by DizzyTech on 2007-04-04
I Installed Ubuntu in a special way to get it to run from within NTLDR.

Basically, I split my 40GB hard drive into four partitions:  one NTFS drive for Windows, one ext3 for root, one swap for swap, and another ext3 for boot.  In the Ubuntu installer, I told it to install GRUB to the boot partition, /dev/sda4.  From there, I mounted my Ubuntu partition (/) and used dd to copy the boot loader to that partition.  From there, I used the ext2 driver in Windows to copy to loader to the C: drive, and set boot.ini to load Ubuntu from that loader file, so I could keep Windows safe.

If the above doesn't make sense, I just did what GRUB does automatically in reverse:  I boot into Ubuntu from NTLDR, also known as chainloading.

Now, I would like to get rid of that boot partition, and possibly even overwrite the MBR with Grub.  I know I can do that with grub-install.  I also understand that GRUB can chainload into NTLDR.

Okay, then, so how would I unmount /dev/sda4 from /boot, and get the boot contents to /boot, and then get my computer to boot from there?  Would I have to reinstall Grub ('cause I will!)?

I prefer to not reinstall Ubuntu, as I have got a lot of tweaks set up and don't want to have to reinstall when Feisty comes out.  And, yes, I want to keep Windows, sadly, but I prefer to use Ubuntu and want to give it Master Boot Record dominance over Windows.

:redface:

---

### Post by trent dillman on 2007-04-04
...

---

### Post by DizzyTech on 2007-04-04
Is that all?  I guessed that would be the solution, I just wasn't sure.  Can anybody confirm this, because I'll do it in five minutes.

---

