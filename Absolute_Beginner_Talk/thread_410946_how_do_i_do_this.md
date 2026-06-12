---
title: "how do i do this?"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by ayonguha on 2007-04-16
hi all,

a very good evening (it is evening in Australia.....)

i have just got a ubuntu CD. traditionally i have been usin windows and am now willing to be a convert...have had enough of microsoft taking all my money (im a uni student)....

my questions are fairly simple (and may be stupid)....

*  presently i have windows xp home on my computer with all my data (projects, assignments and stuff...) so i dont want to loose it.

* i have today purchased an external drive to use it dedicatedly for ubuntu......

my questions are:

1) how do i load ubuntu and make sure that it is only on my external hard drive?
2) when i want to run ubuntu and NOT windows....how do i do it?

sorry guys....im very new and may be asking stupid qstns.....but please help...

Ayon

---

### Post by ayonguha on 2007-04-16
Double post.

---

### Post by dstew on 2007-04-16
I would recommend installing Ubuntu on your regular hard drive, and using the external drive for storage. You can install Ubuntu on an external drive, but there can be frustrating issues to solve to get it working.

When you install Ubuntu, it will install the GRand Unified Boot Loader (GRUB) that will let you boot either Windows or Linux. A menu comes up when you boot that gives you the option to boot Ubuntu or Windows. Even if you install Ubuntu on your external drive, you should install grub stage 1 on your regular hard drive. It overwrites the Windows boot loader in the Master Boot Record (MBR), and this makes some people nervous, to the point that they try to get all of Ubuntu booting directly from the external drive. This will cause problems in most cases, because of the difficulties computers have in booting external drives. It is much better to be brave and install grub on the regular hard drive. If for any reason you want to put the Windows boot loader back into the MBR later, you can do it with the fixmbr command from the Windows recovery console on the Windows recovery CD.

EDIT: If you put Ubuntu on the external drive, but want to boot Windows from the hard drive with grub **when the external drive is unplugged** you will have to make at least a small /boot partition on the hard drive. Grub will need to have this partition available in order to use its menu file, to boot Windows.

---

### Post by Happy_Man on 2007-04-16
dstew is right, just do exactly as he says.

---

### Post by NESFreak on 2007-04-16
Do you want it to work only on your pc or on any pc you plug your hd in?

for something similar to your live cd, thoug storing your personal settings:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent). (kinda complicated for a newby)
if you plug in your external harddrive and reboot your pc it would then start automatically on any pc. (well if your bios is configured from booting from usb that is. Sometimes you need to press some key to get a boot menu)

NESFreak

---

