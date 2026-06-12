---
title: "Remix OS security concerns in light of Meltdown and Spectre"
date: 2018-01-13
forum: Any Other OS
---

### Post by jadaube2 on 2018-01-13
I installed Remix OS on a couple machines running Ubuntu (both have been upgraded to 17.10) using the dual boot instructions posted by Deepak.  See [https://medium.com/@deepakpk/how-to-dual-boot-remixos-with-ubuntu-c7ee2d973f72](https://medium.com/@deepakpk/how-to-dual-boot-remixos-with-ubuntu-c7ee2d973f72) The nickel version of this set up is you drop the kernel, ramdisk image, system image, and initrd.img into its own folder and then tell grub how to boot it all up by adding a menu entry through /etc/grub.d/40_custom. There is no separate partition, just a separate folder on the ubuntu partition.  When Remix OS boots up, it can access other partitions on my drive, but it cannot read the ubuntu partition from whence is booted (it shows up as "Corrupted").

Jide is no longer developing Remix OS, so it seems unlikely that they will release any patches to mitigate spectre and meltdown.

Does any one know if it's possible to manually install android patches and updates? If not, is there any chance this vulnerability could be used to access information in the Ubuntu file system or somehow negatively affect the computer when Ubuntu's booted up?

---

