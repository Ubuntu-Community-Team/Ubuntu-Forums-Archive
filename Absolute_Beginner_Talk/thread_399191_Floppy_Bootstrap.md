---
title: "Floppy Bootstrap"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by flyby4 on 2007-04-02
Hi,
I am just looking at reestablishing a Linux partition on my PC.  I used Red Hat some time ago (years) and vaguely remember there being an option to have a floppy bootstrap instead of using LILO.  Unfortunately, I share the PC and while I have added a seperate harddrive for Ubuntu I need to be able to boot into Ubuntu from a removeable media if possible.  This used to be discussed in the install instructions for RedHat but I can't seem to find the equivalent in Ubuntu.  Any suggestions?

Steve

---

### Post by dstew on 2007-04-02
You can make a bootable floppy, with either LILO or grub. For a grub floppy, see:

[http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy](http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy)

There is also the SuperGrub disk, which can also be made into a bootable floppy:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If you want to boot from a floppy, it might be best to use the Alternate Install disk, because it asks you more directly about how you want to boot. The Live CD install assumes you want to install grub on the first hard disk.

---

### Post by flyby4 on 2007-04-02
Thanks dstew.  That is exactly what I wanted to know.  I got burnt badly last time I installed unix so am being more careful this time.

---

