---
title: "[SOLVED] Safely eliminating Vista on First Hard Disk"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by lyndaj70 on 2007-11-02
Hello,
 I have installed Ubuntu on my secondary hard disk, with Vista currently occupying my first hard disk.

I want to delete the Vista install, and just move /home over to that drive.

I know how to use gparted to delete the partitions in the other drive, but am concerned because it is the primary drive.

I really don't want to tear into the system physically, or reinstall.

Can I safely delete the partitions in the first hard disk, delete the grub entries, and not have to fear having a system that won't boot?  In other words, which hard disk is the stupid MBR on that contains GRUB?  I want to boot from the secondary hard disk.

I am including screenshots of my disk structure.

Any tips would be appreciated.

Thx, ~L

---

### Post by anliveyak on 2007-11-03
on most systems you have to have the boot disc on the master not the slave. so just put the disc with ubuntu on the master and boot from it, format the other drive, and minipulate it from there.

---

### Post by p_quarles on 2007-11-03
If GRUB is located on the first disk then, yes, formatting will screw up the system. The good news is that it's easy to repair. You can use an Ubuntu live disk to reinstall GRUB.

If that fails, you can use the "Super GRUB disk" (link below) as a more foolproof fix. Just make sure to burn a copy before you  procede.
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by lyndaj70 on 2007-11-03
I'm not quite sure where Grub is.... Is there any way to find out?

And how would I use the Live CD to repair Grub?  Would you just use the recovery mode?

---

### Post by p_quarles on 2007-11-03
No, just a regular live bootup is fine, and then open a terminal. Further instructions here:
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by lyndaj70 on 2007-11-03
> **p_quarles said:**
> No, just a regular live bootup is fine, and then open a terminal. Further instructions here:
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

Thank you very much for the help!

I went in, swapped hard disks, and booted with the live CD, then ran the commands on Grub.

It brought my grub menu back, but still showing that Ubuntu was still on the secondary hard disk I got a boot error.  That was an easy fix.  Just had to edit grub again, only this time without the livecd. So now I have a straight Ubuntu PC, booting correctly, Yay!  :lolflag:

Now on to repartitioning that 80 GB drive and moving /home to it...

Thank you so much again!  You deserve some :popcorn:

~L

---

