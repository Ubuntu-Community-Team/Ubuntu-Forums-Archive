---
title: "boot option, change default disk? in open firmware?"
date: 2013-02-19
forum: Apple Hardware Users
---

### Post by stevewasiura on 2013-02-19
hello, i have G5 dual boot with ub 12 desktop & macOSx installed. i can hold down the option key to select which os i want to boot from, but the Mac OS is the default. i want to change this to default to UB12

i have read a bunch of stuff about open firmware and think i am on the right track. :P

but i need an explanation of the type of boot file i need to include at the end of the boot command.


using open firmware, the boot device is set to the hard drive with macos installed on it. i have UB12 on a separate sata drive, sdb

using ub12 terminal and fdisk -l cmd, i have these partitions on sdb:

1 map
2 boot
3 native
4 swap
5 free

using OF, i have found the sdb in the device tree at

/ht/pci@7/k2-sata-root@c/k2-sata@1/disk@0

using OF, i have found two aliases to that path:
ultra1 
 and 
sd1

therefore i try the boot cmd inside OF
  boot sd1:2, \\:tbxi
(because partition 2 is labeled boot) but it does not work.

i've read more and learned that \\:tbxi is the filetype for macos, so that is probably incorrect to use in my situation.

should i use something like 
 , /boot/vmlinux  or ,/yaboot ?

Questions:
1. or is there a different way I'm supposed to change the default boot device and boot volume?

2. is yaboot automatically installed by UB12 on PPC dual boot?

3. is there a way i edit yaboot to change my default disk loaded by OF?

thanks

---

### Post by rsavage on 2013-02-20
The links here may help you [https://wiki.ubuntu.com/PowerPCFAQ#I.27ve_lost_yaboot.2C_what_can_I_do.3F](https://wiki.ubuntu.com/PowerPCFAQ#I.27ve_lost_yaboot.2C_what_can_I_do.3F)

---

