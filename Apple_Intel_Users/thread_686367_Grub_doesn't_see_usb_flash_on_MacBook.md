---
title: "Grub doesn't see usb flash on MacBook?"
date: 2008-02-03
forum: Apple Intel Users
---

### Post by PaulFXH on 2008-02-03
I'm using a MacBook C2D with rEFIt installed to allow me to boot various Linux OSes (including Gutsy).
While most of the OSes are located on the internal HD, two are installed on an external usb HDD.
For these latter two, the kernel files (vmlinuz and initrd.img) are stored along with the bootloader (Grub) on the Ubuntu root partition on the internal drive and everything works fine.
So, what's the problem?
Well, I have a 4 GB usb flash drive on which I have installed Puppy linux and I can boot this on my desktop (old dell Dimension 4550). How I get it to boot is exactly the same as I've described above for the MacBook (through the Ubuntu root partition where its kernel files are stored).
When I try to boot to Puppy on the usb key on the MacBook, however, I can't. It seems that the usb key partitions (2 partitions, vfat) are not recognized as block devices.
So while on the desktop the usb key partitions are available in /dev as /dev/sdb1 and /dev/sdb2, nothing at all equivalent shows up when I try the same thing on the Mac.
Nevertheless, rEFIt does see something as THREE additional icons show up on the rEFIt boot menu. I presume these are what are called (on the desktop) /dev/sdb, /dev/sdb1 and /dev/sdb2
Of course I can't boot to any of these from the rEFIt page for the usual reasons (mac firmware doesn't like usb stuff -- or something equivalent).
Does anybody know if it is at all possible for Grub to recognize my usb flash drive as bootable on the MacBook?
Thanks
Paul

---

