---
title: "Defaults location for apt-get/dpkg when installing packages"
date: 2005-12-20
forum: Absolute Beginner Talk
---

### Post by phillyboy on 2005-12-20
This is more of an annoyance than anything, but I was wondering where the configuration defaults for certain programs are that dpkg/apt look at when installing packages?

My situation is this, whenever I install a new kernel, /boot/grub/menu.lst gets automagically modified to put in a reference for the new kernel, which is fine by me. However, sometime between installing and running ubuntu, my / partition moved from hda6 -> hda10 (I was moving partitions around trying change a couple from ntfs -> ext3, everything works fine now thogh ;) ). When I all things were done, I made sure to update grub's menu.lst file so that root=/dev/hda10...however, every time I install a new kernel and menu.lst gets updated to put in the new reference, ALL of my root=/dev/hda10 lines get changed back to root=/dev/hda6! 

Is there any way to change some default config file being parsed so that this never happens anymore? Thanks for any help! (I will be back in 2 1/2 hours to peek in on this thread again)

---

