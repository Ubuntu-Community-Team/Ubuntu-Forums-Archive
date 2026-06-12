---
title: "bootloader install fail on external hard drive"
date: 2005-04-13
forum: Apple PPC Users
---

### Post by eduardgrebe on 2005-04-13
I install hoary on an external firewire drive (an iPod, actually) on my Powerbook G4. I let it wipe the entire disk and autoconfigure partitions. This creates 3 partitions: boot swap and ext3.

When the installer gets to the bootloader install stage it simply states "bootloader failed to install" (or yaboot failed to install, i don't remember) and then gives me instructions for manually booting.

Has anyone else had this problem, or know why this could be happening? Thanks.

---

### Post by interrupt on 2005-05-05
I had the same problem. It is not possible to install to an external firewire drive properly due to booting issues - as you have found. However, you can get around this by first creating a working installation (say on the internal powerbook drive), then creating another installation on the firewire drive that will boot via a ramdisk. Once this is working and you are happily booting from the firewire drive, the first installation, on the internal drive, can be got rid of.

I posted a brief outline of this [here](http://www.ubuntuforums.org/showthread.php?t=29837) 


cheers

---

