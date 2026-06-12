---
title: "Freezing at splash screen"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by spunemaster on 2007-03-16
When it boots up and shows the splash screen, the computer just stops loading. I think there are some hardware compatibility issues. The computer boots fine in Live CD mode though.

2.8ghz P4
Intel 875P motherboard
1GB Corsair RAM
Hitachi 160GB SATA 

Perhaps there's something wrong with the partition table. The hard drive I'm over writing has Vista installed. I have deleted the partition in QTParted.

---

### Post by Rizlaw on 2007-03-16
> **spunemaster said:**
> When it boots up and shows the splash screen, the computer just stops loading. I think there are some hardware compatibility issues. The computer boots fine in Live CD mode though.

2.8ghz P4
Intel 875P motherboard
1GB Corsair RAM
Hitachi 160GB SATA 

Perhaps there's something wrong with the partition table. The hard drive I'm over writing has Vista installed. I have deleted the partition in QTParted.

I've read that VISTA really won't play nice with Linux because of the way it writes to the MBR of the hard disc. Since, using the Ubuntu LiveCD doesn't touch your VISTA installation, it makes sense  that it works. IMO, what you should do if you are over writing VISTA, is first to boot with a DOS or WIN98 boot floppy disc and at the dos prompt execute the command "fdisk /mbr" to overwrite VISTA's mbr info. Then try to reinstall Ubuntu from the LiveCD. I think that should work.

---

### Post by spunemaster on 2007-03-16
After about 10 minutes on the splash screen, a message says:

/bin/sh: can't access tty; job control turned off
(initramfs)

I'm also going to manually partition the hard drive rather than letting Ubuntu do it automatically.

---

