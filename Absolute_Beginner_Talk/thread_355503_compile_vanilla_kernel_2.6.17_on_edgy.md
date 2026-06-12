---
title: "compile vanilla kernel 2.6.17 on edgy"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by maneesh on 2007-02-07
Hi,  I wanted to kick off on some kernel hacking and so  I compiled a vanilla kernel 2.6.17.10 (downloaded from kernel.org),  I followed this method [http://www.falkotimme.com/howtos/debian_kernel2.6_compile/](http://www.falkotimme.com/howtos/debian_kernel2.6_compile/)

The kernel compilation was successful (I used the old configuration file, and did no modifications to it), and then I installed new kernel, prepared initrd, modified grub, and then while I tried booting up with this kernel, I couldnt .. It said (i think in early bootup) that it couldnt load ext3 module, and so panic. 
Any idea what could be going wrong with me.

Thanks

---

### Post by resist- on 2007-02-07
It sounds like you did not compile the ext3 module... Ext3 is a filesystem, and the kernel needs an option to be activated to be able to access your hard disk.  You should be able to include it as a module in your kernel config (don't remember where the option is). Enabling the module for  ext3, and recompile the kernel should do the trick...

Good luck :)

---

