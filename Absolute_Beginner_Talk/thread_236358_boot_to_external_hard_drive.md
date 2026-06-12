---
title: "boot to external hard drive"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by yanqui on 2006-08-14
I have successfully installed Ubuntu on an external hard drive.  I never saw anything about a GRUB menu or anything, so when I took out the CD to try to boot to it, it boots straight from the hard drive; I have the BIOS set to boot from the removable device first, but there's nothing to tell Linux to load.

Obviously I missed a step, I don't know where, but how do I remedy this?  I want to keep my windows hard drive intact and have the option to choose the Linux system whenever the external USB drive is attached.  How do I do that?

---

### Post by lamego on 2006-08-14
The desktop CD does not allow you to sepcify where to install grub, you would need the alternate CD for that.

Are you refering to an USB external disk ? Please be ware that it is not trivial to boot from an external USB device, there is some community docs on how to do it:
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by yanqui on 2006-08-14
Yes, it is a hard drive in an external drive case, with a USB connection.  BIOS supports booting from USB devices, and at this point, I can't even GET to the Ubuntu installation on that other drive because Windows recognizes that there's a drive there but not what's ON it.

---

### Post by yanqui on 2006-08-15
Okay, I guess I'll just stick with Windows.  I know, the Linux gurus will tell me it's baaaaaaaaaaaad.  Well, IT'S running, and Ubuntu ISN"T.

---

### Post by yanqui on 2006-11-13
Update after three months.  Ubuntu is installed on the usb external drive.  Grub is loaded there.  When I try to boot to it, I get the following message:

Booting 'Ubuntu, kernel 2.6.15-26-386'

root (hd0,0)
Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/sdb1 ro quiet splash

Error 17: Cannot  mount selected partition
Press any key to continue...

any ideas?

---

### Post by mo79 on 2006-11-13
> **yanqui said:**
> Update after three months.  Ubuntu is installed on the usb external drive.  Grub is loaded there.  When I try to boot to it, I get the following message:

Booting 'Ubuntu, kernel 2.6.15-26-386'

root (hd0,0)
Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/sdb1 ro quiet splash

Error 17: Cannot  mount selected partition
Press any key to continue...

any ideas?

hd0,0  is probably your Windows hard disk and partition. You want it to point to your external drive. Alas, I don't know what that would be. Someone carry the baton... :neutral:

---

### Post by keithweddell on 2006-11-13
I think it's probably going to be (hd1,0).  You'll need to edit /boot/grub/menu.lst file to change this so you'll probably need to boot from a livecd to mount the external drive and access the file.

Keith

---

### Post by yanqui on 2006-11-13
I'll try that next.  thanks.

---

### Post by cotcot on 2006-11-13
If you do not get out of this you can copy the liveCd to your external USB drive and make it persistent using the instructions from the link in my signature. I have used it several times and it works fine.

---

### Post by yanqui on 2006-11-14
Does that enable you to boot the host computer without being connected to the usb drive?  At this point I'm not sure if I screwed up the instructions and installed the grub in my mbr (I tried not to do that) or if it's just going to be that way, that I always have to have the usb drive connected to boot.  That's not what I wanted to achieve.

---

### Post by yanqui on 2006-11-14
As it turns out, I had in fact installed the GRUB to the mbr.  I was able to fix the mbr, but now I still don't have a bootable ubuntu on the external hard drive.  Trying to figure out the right order to load these modules:

ehci-hcd
uhci-hcd
usb-storage
usbcore
usbhid
scsi_mod
sd_mod

Any ideas?  the above was one order that worked for one user; a different order worked for another; I've tried them both.  Knowing only that they have to do with usb drivers and scsi drivers, I'm not sure what order would work best, so I guess I'll just play around and find the right order.

---

### Post by yanqui on 2006-11-15
Okay, I have it installed and I can successfully boot to the linux system on the usb drive, and when it's disconnected, it boots automatically to windows.  While it was installing, I had it configure the NIC; but I can't seem to get out on the internet, which I was able to do when the grub was on the mbr.  The dns address is correct.

Any ideas?](*,)

---

### Post by yanqui on 2006-11-15
Got it!!! Sitting here typing in firefox via the usb hard drive connected to my laptop.  And no, I don't know what I did that fixed it--I simply rebooted; but then, that solves a lot of unknown problems.

---

