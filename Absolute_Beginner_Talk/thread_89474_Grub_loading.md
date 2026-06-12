---
title: "Grub loading?"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by davidgypsy on 2005-11-12
This is my Grub menu.lst:


title        Ubuntu, kernel 2.6.12-9-686-smp 
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.12-9-686-smp root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.12-9-686-smp
savedefault
boot

title        Ubuntu, kernel 2.6.12-9-686-smp (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.12-9-686-smp root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.12-9-686-smp
boot

title        Ubuntu, kernel 2.6.12-9-386 
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.12-9-386
savedefault
boot

title        Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.12-9-386
boot

title        Ubuntu, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title        Ubuntu, kernel 2.6.12-9-386 (on /dev/hdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash 
initrd        /boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title        Ubuntu, kernel 2.6.12-9-386 (recovery mode) (on /dev/hdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro single 
initrd        /boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title        Ubuntu, memtest86+ (on /dev/hdb1)
root        (hd1,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title        Ubuntu, kernel 2.6.12-9-386 (on /dev/hda2) (on /dev/hdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash 
initrd        /boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title        Ubuntu, kernel 2.6.12-9-386 (recovery mode) (on /dev/hda2) (on /dev/hdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single 
initrd        /boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title        Ubuntu, memtest86+ (on /dev/hda2) (on /dev/hdb1)
root        (hd1,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title        Ubuntu, kernel 2.6.12-9-386 (on /dev/hdb1) (on /dev/hda2) (on /dev/hdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash 
initrd        /boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title        Ubuntu, kernel 2.6.12-9-386 (recovery mode) (on /dev/hdb1) (on /dev/hda2) (on /dev/hdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro single 
initrd        /boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title        Ubuntu, memtest86+ (on /dev/hdb1) (on /dev/hda2) (on /dev/hdb1)
root        (hd1,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

...but when booting it just tells me that Grub is loading, but it doesn't. I have tried everything I can find on this forum, I also tried grub-install command in recue mode, and update-grub... Any ideas? :confused:

---

### Post by apjone on 2005-11-12
on the ubuntu cd should be a Smart boot manager or SBM , dd this to a floopy disk or use floppy emuolation and burning to cd , this can be use to bypass grub

---

### Post by davidgypsy on 2005-11-12
[quote=apjone]on the ubuntu cd should be a Smart boot manager or SBM , dd this to a floopy disk or use floppy emuolation and burning to cd , this can be use to bypass grub[/quote]

Fortunately I rescued the grub boot menu from the installation on hda2, so I can boot my new installation on hda1. But I want to remove hda2 and use it elsewhere... How do I get Grub to behave?

---

