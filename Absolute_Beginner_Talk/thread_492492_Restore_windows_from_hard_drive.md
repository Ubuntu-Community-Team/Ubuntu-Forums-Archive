---
title: "Restore windows from hard drive"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by metalaxesucks on 2007-07-04
Hello folks. I'm trying to restore a computer using the back up on the hard drive (if there is one on the hard drive, and it it is possible). Before you tell me to use my restore CD, let it be known that my CD Rom is NOT WORKING AT ALL, so that is not an option.
Here is a picture of my partition.
[http://www2.hawaii.edu/~hurtadoj/diskman.jpg](http://www2.hawaii.edu/~hurtadoj/diskman.jpg)
It looks like there may be a backup on the smaller partition.Can somebody tell me how to do it - if it is possible.
Thanks

---

### Post by p_quarles on 2007-07-04
Try looking for clues in the BIOS menu as you boot the system. On an HP system, you just need to press F12 to boot from the recovery partition. 

That said, you should also know that a Windows reinstall will delete your GRUB file, so if your CD-ROM drive isn't working you may not be able to get into Linux again.

EDIT: And I know all of this because I'm about half-way through the process of recovering my own dual-boot system. I feel your pain. :-)

---

### Post by lisati on 2007-07-04
On my COMPAQ machine (COMPAQ are owned by HP) it's F10.  If you're given a chance, do a "non-destructive restore" first so you're in with a chance of getting your data files back (if they're still there)

---

