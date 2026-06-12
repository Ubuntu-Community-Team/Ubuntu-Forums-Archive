---
title: "adding OS to grub"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by siralphred on 2007-11-01
i installed mac on my external usb drive and cannot seem to be able to include it in my grub.list. Right now i have Vista(hd0,0) and Ubuntu(hd0,2)on my internal drive and would like to be able to add my external usb drive to my grub. Accordin to vista the external drive is on Disk 3 and the partition i installed mac on is 2.   i added  MacOS 10.5 (hd3,1) to grub but it tells me its the wrong disk..any help?

---

### Post by gate on 2007-11-01
Disk 3 would be hd2  (0 then 1 then 2). Its a zero based list (hence the reason your internal is hd0)

---

### Post by siralphred on 2007-11-01
yeh but i added (hd2,2) and still got an error btw i looked at the external drive with partition editor and its "name" seem to change every time sometimes sdc1 and sometiems sdb2 etc

---

### Post by gate on 2007-11-02
in Linux, "sd[a-z]" refers to SCSI/SATA/USB drives. Grub referrs to all drives as hd#, it could be hd1 I would check that first. Then what I would do is plug the usb drive in before booting. Then run "sudo grub-install --recheck --root-directory=/ /dev/hda"

 I use this when I need it to autocheck for OSes/partitions. 

 It *might* work. I have used Ubuntu on a USB drive, I put the boot loader on the USB from the install and set the BIOS to prefer USB.

---

### Post by siralphred on 2007-11-02
> **gate said:**
> in Linux, "sd[a-z]" refers to SCSI/SATA/USB drives. Grub referrs to all drives as hd#, it could be hd1 I would check that first. Then what I would do is plug the usb drive in before booting. Then run "sudo grub-install --recheck --root-directory=/ /dev/hda"

 I use this when I need it to autocheck for OSes/partitions. 

 It *might* work. I have used Ubuntu on a USB drive, I put the boot loader on the USB from the install and set the BIOS to prefer USB.

thanks for the hint...Trying hd1 gives the error "selected disk doesnt exist". For more clarity, i have included a pic of my partitions as seen by partition editor the top one is my internal drive, that has vista and ubuntu and the one below is the external usb drive that i have installed mac os to but cannot add to grub. This is how my grub looks at the moment:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=90815104-d7d5-4c8c-a30b-36ab1abea090 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=90815104-d7d5-4c8c-a30b-36ab1abea090 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

