---
title: "Command Line Help"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by PureNRG on 2007-10-20
My current setup for my harddrive is sadly at a half-installed version of Ubuntu which crashes every time I load it. :(
I have my 5.10 cd which I want to use to reinstall Ubuntu without hopefully losing power this time, but I have no idea how to load the cd with root level command line.. and yes, I did change the BIOS to boot from CD first, but currently it's apparently ignoring the cd during the boot sequence. :mad:


Thanks all.
-Zach

---

### Post by eklypsd on 2007-10-20
Can you access a boot menu during startup (usually by pressing F12)? Some manufacturers disable this and needs to be enabled inside the bios. You could also change the boot order to boot from CD first while inside the bios.

---

### Post by PureNRG on 2007-10-20
[QUOTE="PureNRG"].. and yes, I did change the BIOS to boot from CD first ..[/QUOTE]

One step ahead of ya on that part. :)
But is there something I can type at the command line as the Root user to somehow boot the CD and reinstall Ubuntu?

---

### Post by eklypsd on 2007-10-20
Check this link out: [https://help.ubuntu.com/community/SmartBootManagerHowto]("https://help.ubuntu.com/community/SmartBootManagerHowto")

Ubuntu uses the Smart Boot Manager (SBM) which is loaded by the bios. Sometimes this can fail to initialize on older systems or bios that doesn't support isolinux. instead of booting on the CD directly, you can create a SBM floppy image by using the sbm.bin disk image. You can create a floppy that will detect your CDROM and let you boot on it bypassing any BIOS limitation.

---

