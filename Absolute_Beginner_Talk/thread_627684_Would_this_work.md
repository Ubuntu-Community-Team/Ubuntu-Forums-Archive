---
title: "Would this work?"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2007-11-30
I've got my gaming machine wiht Vista 64 bit loaded in a  software RAID1 config on two WD raptors.  If i put another drive in an loaded ubuntu and installed the MBR to it, would i still be able to boot the vista partition?  Thanks for the help.

---

### Post by quandary on 2007-11-30
Why don't you just install your drive, and then install Ubuntu AND Grub on this drive?

You can then load Ubuntu via the Vista bootloader. You can use EasyBCD to work with the Vista bootloader. It's freeware, completely graphical and not difficult at all AND IT WORKS!

---

### Post by ptn107 on 2007-11-30
So you want Vista 64 on the RAID and Ubuntu to not be?  I've dual booted Vista and Ubuntu both on the same RAID volumes with success.  I don't know about doing them separately.  It may mess up the MBR (though I'm not 100% sure on this one).  Anyone?

---

