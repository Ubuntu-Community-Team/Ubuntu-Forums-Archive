---
title: "rEFInd doesn't want to boot from newer kernel version automatically"
date: 2015-09-30
forum: Apple Hardware Users
---

### Post by Tenn1518 on 2015-09-30
I have a Macbook Pro 12,1 (early 2015) dual booting Ubuntu 15.04 and Mac OS X with rEFInd. It works close to perfect, and the new Linux kernel update made it even more perfect. The Macbook Pro 12,1 introduced the Force Touch trackpad, and Ubuntu didn't support it very well. I could move the mouse cursor and click, but scrolling with two fingers or right clicking with two fingers didn't work. This was on kernel 3.19. I updated recently to kernel 4.2.2 and it worked. The trackpad now can right click and scroll, but unfortunatelly rEFInd wants to boot from the 3.19 kernel. The new 4.2.2 kernel is also installed, but rEFInd boots from 3.19. I can still boot 4.2.2 in rEFInd by pressing F2 while choosing Ubuntu and choosing the option to boot from 4.2.2 generic, but I would like to be able to automatically boot from 4.2.2 without needing to press F2 and selecting 4.2.2. I also have 4.2 installed and I don't need that, so I want to delete 3.19 and 4.2. I can still boot properly from either kernel, but I lose the trackpad functions and I need the trackpad functions.

---

### Post by imattux on 2015-09-30
This  is an educated guess. I decided not to use rEFInd because booting  directly from EFI involves the same number of steps, and Rod Smith himself (rEFInd's creator/maintainer) provides instructions for doing it.

Based on Rod Smith's answer [here]("http://askubuntu.com/questions/321257/how-to-delete-refind-entries")  (from 2013, but still relevant), I think that what you should do is  remove the older kernels from the boot partition and edit/update the  refind config file accordingly. You might want to backup the old kernels  to another location rather than deleting them, but it sounds like 4.2.2  is working just fine. All you need to do is make the 4.2.2 kernel the first and/or only Linux choice that rEFInd can find.

Please let me know if that does the trick, I'm pretty sure but would love confirmation

---

### Post by Tenn1518 on 2015-10-03
> **imattux said:**
> This  is an educated guess. I decided not to use rEFInd because booting  directly from EFI involves the same number of steps, and Rod Smith himself (rEFInd's creator/maintainer) provides instructions for doing it.

Based on Rod Smith's answer [here]("http://askubuntu.com/questions/321257/how-to-delete-refind-entries")  (from 2013, but still relevant), I think that what you should do is  remove the older kernels from the boot partition and edit/update the  refind config file accordingly. You might want to backup the old kernels  to another location rather than deleting them, but it sounds like 4.2.2  is working just fine. All you need to do is make the 4.2.2 kernel the first and/or only Linux choice that rEFInd can find.

Please let me know if that does the trick, I'm pretty sure but would love confirmation
Thanks! It worked. I just needed to delete the kernels from ~/boot, rEFInd didn't remember the old kernels and only offered me the option to boot from the 4.2.2 kernel. I would like to know a way to automate this process so I don't have to delete old kernels every time I update, but for now just moving the kernel files works.

---

