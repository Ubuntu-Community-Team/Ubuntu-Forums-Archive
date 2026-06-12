---
title: "Need a how-to for beige G3 install"
date: 2005-11-20
forum: Apple PPC Users
---

### Post by eagle15 on 2005-11-20
I've got a beige g3 server with 6mb scsi drive and a dvd-rom running OS 8.6 with 384mb ram, 400mhz g3 and 16mb ati rage 128 pci video card.  OS 8.6 is pretty snappy but is also useless.  The newest browser I could get for this is Netscape 6.  I'd like to upgrade to linux so I downloaded ubuntu 5.10 live cd and am trying to get it running.  I put the kernel image from the cd into bootx 1.2.2 kernel directory and put the initrd.gz file into the bootx directory and renamed it to ramdisk like a previous thread here mentioned.  When I try to run bootx it shows info about the kernel and promptly hangs.  Upon reboot I get a message telling me no suitable kernel is available and that there is some sort of error on line 1061 I believe.  I am now looking for a detailed howto on this subject.  My limited hacking skills are failing me.  Thanks for any info.

eagle15

---

### Post by ristosu on 2005-12-09
BootX "Linux Kernels" folder should be placed in "System Folder". Then put the vmlinux (kernel) and the initrd.gz (it can be picked from anywhere by BootX) there. When booting (if you have the BootX extension in "System\Extensions" folder), BootX starts and finds the kernel. With "Options" button you can choose the initrd. And, finally, for live cd, you have to add to kernel arguments:

"casper/enable=true casper-udeb/snapshot/backing-file=/cdrom/casper/filesystem.cloop --"

There is also a "Save to prefs" button. Press it before pressing "Linux" and BootX will remember the settings.

The other variant of BootX, BootX application, should be placed in "System Folder\Control Panels". It works like the extension after the system has booted.

---

