---
title: "Booting Ubuntu from a Mac Mini"
date: 2013-03-27
forum: Apple Hardware Users
---

### Post by williepabon on 2013-03-27
I have a bootable usb hard disk with Ubuntu12.04 that I want to connect and boot from my Mac mini, that hasMountain Lion OS. I've heard that this is possible to do using boot managers like rEFInd. I don't have any experience on this and will like to know If somebody has done this before and can share his experience. Thanks.

---

### Post by pindar on 2013-03-27
Depends on what you mean when you write "bootable usb hard disk." If you want to boot an (intel) Mac from an external hard disk, it must have a GUID partition table. If you install grub-efi to such a disk, you can actually boot a Mac from it; if you follow the correct naming scheme for the efi binary, you don't even need refit or refind, you can use the Apple boot loader (see [https://help.ubuntu.com/community/UEFIBooting#Using_Apple_bootloader_itself_.28safest_option.29]("https://help.ubuntu.com/community/UEFIBooting#Using_Apple_bootloader_itself_.28safest_option.29")).

---

### Post by williepabon on 2013-03-27
pindar:
Thanks for answering. Maybe I didn't explain myself clearly. When I said a bootable hard disk I'm referring to an external hard drive where I installed Ubuntu 12.04, that now is connected to one of the usb ports of a Windows XP desktop. I have the BIOS on the pc to first look for a bootable device on the usb ports, and then GRUB kicks in. My intention is to move that hard drive to my Mac mini (that is newer) and be able to boot in a similar way that I do now on the pc. Just want to know what I have to do on the Mac to make this thing possible. Thanks.

---

### Post by pindar on 2013-04-02
Hi,

well, sorry to say, but again: depends on what you mean when you write "My intention is to move that hard drive to my Mac mini." If you simply want to take the same drive and reformat it, that is doable. It involves a few steps (I have just written [a small tutorial]("http://ubuntuforums.org/showthread.php?t=2131643") on what you have to do), but it isn't too complicated. If you mean "take this drive as it is now and boot a mac from it": I don't think this is possible.

HTH

pindar

---

### Post by williepabon on 2013-04-02
Pindar:
I should not have said "move the hard drive to the Mac mini". Instead, I should have said, "connect the hard drive to one of the usb ports of the mac mini". Then, do something to the Apple boot loader ( if that is possible) so that it could be able to recognize a different file system (Linux) and be able to boot it. If that is not possible, then you answered my question. Thanks.

---

