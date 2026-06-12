---
title: "Hard Drive Issue"
date: 2005-08-19
forum: Absolute Beginner Talk
---

### Post by Mickygor on 2005-08-19
I installed Ubuntu on my second hard drive back in April to try and fix some issues with my Windows installation. However, before I could fix all of them, my dad sent the computer off to a repairs company, who solved the Windows issue with many formats and tweaks. This has left me with absolutely no access to my hard drive except in the BIOS.

Can you help me formatting that drive, and gain access to it again, please?

---

### Post by glug101 on 2005-08-19
Hmmm...
    How to fix this depends a little bit on the end result that you would want.  When you say 'formatting' the drive, it sounds like you want to reformat the partition for use.  This is fairly straight forward and can be accomplished by [list=a]
[*]Partitioning and formatting the drive using the good old DOS fdisk and format commands
[*]Reinstalling Ubuntu (suggested)
[/list] 

If you are interested in keeping the information on the drive, then you might want to use a good livecd (You might want Ubuntu, but I have experience with the Gentoo variety).  Mount the partition.  Use the ```
chroot /[mounted partition] /bin/bash
``` command and then run grub again to get the bootloader working like it did before.

---

