---
title: "Loop in boot during use of Ubuntu server 6.06"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by kortved on 2008-04-09
I do not have much Linux experience, but have tried to install a LAMP server from a CD with Ubuntu 6.06 on a rather small old HP vectra X86/5 cpu with 163 MByte and a 2,6 Gbyte Master HD and a 13 Gbyte Slave HD.
Installation takes some time, and I used the partition-tool during install to erase the hd0 and make the three default "partitions" etc. I chose DK-lanuage, keyboard, gave a username etc.
I succeded in install, at the machine ejected the UBUNTU CD and was ready to reboot.
When it boots, GNU GRUB v 097 writes the following:

root (hd0,4)
kernel /vmlinux-2.6-15-51-server root=/dev/mapper/Ubuntu-root ro quit splash
initrd /initrd.img-2.6.15.51-server
savedefault
boot

.... but the GRUB "boot" cmd gets my HW to boot from start, including the HW/BIOS testing, and then repeating the above root etc ....

What have I done wrong ?
Regards from Kim, a male dane

---

### Post by warbread on 2008-04-10
When is this displaying?  Is it showing on the Grub boot menu, or after Grub has chosen an OS?

---

