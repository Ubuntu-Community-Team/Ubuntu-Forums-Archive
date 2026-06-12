---
title: "GRUB error 21; nothing loads"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by apathos on 2008-01-19
I just tried to install UBUNTU 7.10 on my fathers external hard drive.  He has drive C: with a Windows XP install, and drive D: that we just installed 7.10 to.  (He wanted to put it on the external one to transfer it to another computer)

Ubuntu loads just fine, but now windows ('C:') will not load at all unless the ubuntu drive is attached.

Specifically, when the computer tries to load GRUB step 1.5, it gives error 21 and stops.

All we want now is for this computer to boot normally, no GRUB anywhere (again, he was trying to put ubuntu on a non-networked computer).

Any help is appreciated.

Jeff

---

### Post by gn2 on 2008-01-19
You need to re-write the MBR of the internal drive, there are a few ways of doing so listed under STEP ONE, PREPARE THE MBR on this page:  [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm) This will restore Window's own bootloader.
(You don't need to do step two ;))


When you install to an external hard drive it may not be bootable between different PC's, depending on the hardware.
A better method is to use a "persistent" Flash drive installation, lots of info here: [www.pendrivelinux.com](www.pendrivelinux.com)

---

