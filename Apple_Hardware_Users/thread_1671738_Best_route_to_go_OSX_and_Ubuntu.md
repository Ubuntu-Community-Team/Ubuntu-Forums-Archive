---
title: "Best route to go? OSX and Ubuntu"
date: 2011-01-20
forum: Apple Hardware Users
---

### Post by Abe21599 on 2011-01-20
Ok guys I have a MBP with the latest software (not at it now so not sure on the specifics), everything I need is backed up with time machine, and I have Ubuntu 10.04 on a disc ready to install. Im jsut not sure of a few things
 
Whats the best course of action to get Ubuntu and OSX dual booted on my laptop? bootcamp?
 
id rather erase the main HD and start over on OSX first (clean slate) and then install ubuntu. I have the OSX cds too
 
i try booting off the CD but I dont know what format I need for what partitions
 
Thanks

---

### Post by zero visual on 2011-01-20
Use bootcamp, worked just fine every time I used it, or you could go the virtualbox route?

---

### Post by srs5694 on 2011-01-20
If your Mac doesn't have an nVidia chipset, I recommend against using Boot Camp, since that method creates an ugly and dangerous [hybrid MBR.](http://www.rodsbooks.com/gdisk/hybrid.html) Instead, I recommend you follow [this procedure](http://www.rodsbooks.com/ubuntu-efi/index.html) for installing Ubuntu in a way that will enable it to boot using the Mac's native EFI.

The big caveat here is that nVidia video chipsets reportedly don't work using the nVidia drivers when you boot this way, so you'll need to use the slower fbdev drivers if you've got such a chipset. Thus, if you've got an nVidia chipset, you've got the unenviable choice of using a flaky hybrid MBR or using a slow fbdev video driver.

---

