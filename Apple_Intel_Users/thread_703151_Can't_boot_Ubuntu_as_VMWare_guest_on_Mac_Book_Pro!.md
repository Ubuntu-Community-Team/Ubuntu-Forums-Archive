---
title: "Can't boot Ubuntu as VMWare guest on Mac Book Pro!"
date: 2008-02-21
forum: Apple Intel Users
---

### Post by john.wheeler on 2008-02-21
I have installed Ubuntu 7.10 on a separate partition on my Mac Book Pro, which after some problems with display settings, now works fine.

I would like to run the same Ubuntu installation as a VMWare virtual machine running under Mac OS (using VMWare Fusion).

I have created a new Ubuntu VM from the raw Ubuntu disk partition.

Unfortunately this fails to boot, only getting as far as "running local boot scripts (/etc/rc.local) " 

My guess is that the hardware configuration under VMWare is incompatible with the physical Ubuntu installation. I suspect it might be something to do with the Mac's NVidia video card. I had to download extra drivers to get the native Ubuntu 7.10 to run properly, and obviously the VM image doesn't have these.

Does anyone have any advice on how to get an Ubuntu VMWare guest running on a Mac Book Pro?

Thanks for any help you can give me.

John Wheel

---

### Post by cyberdork33 on 2008-02-21
did you try running in safe mode?
I can't say that many people have made it as far as you have in this endeavor. Also, other errors I have heard of that freeze at that point will continue if you just hit enter.

---

