---
title: "Intrepid MacBook Pro 2,2 does not resume from suspend with attached firewire disk"
date: 2009-01-16
forum: Apple Hardware Users
---

### Post by tp42 on 2009-01-16
I work on a 15" MacBook Pro Core2Duo with an up to date patched Ubuntu 8.10 installation. Suspend worked out of the box, resume works too, except when my macbook is connected to an external firewire disk. 
It suspends but on resume, I could hear the CD/DVD but the screen remains black, no cursor visible and the keyboard is not responsive. So I have to use the power button to turn off/restart the machine.
I face this issue with HFS+ (journaled) formatted firewire 800  and FAT32 formatted firewire 400 disks. The issue appears with a disk mounted before resume and with a disk unmounted before resume.

Is the handling of external firewire disks in the suspend mode not implemented yet as I was used to it ion MacOSX? Do I have to use ext3 formated firewire disks or is there some tewaking necessary to get it working?

uname -a reveils: 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
My model/hardware revision is: MacBookPro2,2
My video card: 01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
My video driver is the "out of the box" ATI/Radeon driver Version 1:6.

I would be happy to try out some hints.

Best regards,
tp42

---

### Post by tp42 on 2009-01-18
Anyone on this?

---

