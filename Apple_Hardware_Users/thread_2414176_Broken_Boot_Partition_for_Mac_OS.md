---
title: "Broken Boot Partition for Mac OS"
date: 2019-03-06
forum: Apple Hardware Users
---

### Post by mickiemck on 2019-03-06
Hello, I need some help as I accidentally broke the boot partition of my macbook air 11” while trying to erase my ubuntu partition and extend the mac partition. I did this by booting ubuntu from a USB and using the “Disks” program to erase the root partition and the swap area and combine the two together. Then, stupidly, I decided to extend the Mac OS X partition usinng that program and not Disk Utility and as a result when I boot, if I enter target disk mode Mac OS no longer appears and only two partitions labelled “windows” and “windows” appear from Ubuntu. If I choose the first it’ll attempt to boot something but remain stuck on the first line flashing with no text while the second partition will simply freeze and hang.

Can anyone help me? I want to avoid having to erase my disk as there was a whole bunch of important stuff on the Mac Partition. If I’m guessing correctly it isn’t “broken” so to speak, but the bootloader no longer sees it. Would there be any way to correct that?

Thanks for any help in advance.

---

### Post by oldfred on 2019-03-06
I do not know Mac, but those that do may want more details.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

