---
title: "First Installation on HP TX2000z"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by gcm on 2008-02-25
I just bought a HP TX2000 tablet PC. It came with Vista Home Premium pre-installed. I srinked the main partition to leave about 26 GB to UBUNTU. First, I tried to install Ubuntu 7.10 64-bit from the Live CD. It did not work out. I received an Hardware error. I read some posting and I started again with the Alternate CD of Ubuntu 7.10 64-bit. I completed the installation, but after restarting the system I received again an hardware error as follows:

Loading hardware drivers ....
HARDWARE ERROR
CPU 0: Machine Check Exception: 4 Bank 4: b200000000079f0f
TSC 115809ae7e
This is not a software problem!
Run through mcelog --ascii to decode and contact your hardware vendor
Kernel panic - not syncing: Machine check


Does anyone know what is going on?
Any help would be appreciated.
Thanks,
GCM

---

### Post by myddewji13 on 2008-02-25
try the 32 bit install..its more stable from what i read...as is your windows is prob 32-bit

---

### Post by gcm on 2008-02-26
I did try. The error message does not appear, but starting UBUNTU I have a blank screen. After a while, the display appears. If I start in recovery mode, I can get the prompt line. Also, after the boot selection it appears a BIOS BUG: PCI. I will try all the peripherals and post the results. Thanks for the hint.

---

### Post by pAt84 on 2008-02-27
Hit F6 when the boot menu comes up and add **noapic irqpoll noirqdebug**.
This did the trick on my tx2050eg. 

However, you should note that the Wacom Digitizer is not supported so far, since it is on the USB bus. I dumped the Ubuntu again and went back to Windows when I noticed that there are huge issues with Ubuntu and external laptop screens.

Pat

---

