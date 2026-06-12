---
title: "Uninstalling Ubuntu through Windows?"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Geohevy on 2008-02-18
I can't get Ubuntu to work on my HP dv6500, so I need to uninstall. My hard drive now has four partitions. My Windows Vista partition, a sizable partition which I think is the actual Ubuntu OS, a 2 GB or so partition which I take to GRUB (which is set to the MBR), and my HP recovery partition.

I'm running put of room, so I gotta get Ubuntu off ASAP. I also cannot boot into Ubuntu with a GUI. Would it be safe to just absorb the 'Ubuntu partition' into the Vista partition? Then would GRUB be left alone, still functioning as the MBR?

How can I go back to the Windows Boot Loader? This laptop came with Vista, so there are no install CDs...

Please help. I need a solution soon... :(

---

### Post by bodhi.zazen on 2008-02-18
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by Geohevy on 2008-02-18
Fixmbr doesn't work on Vista, as far as I know, and I can't access Ubuntu's GUI, so I have no way of opening a terminal...

---

### Post by The Cog on 2008-02-18
After booting Ubuntu, Ctrl-Alt-F1 will get you a text promot (as opposed to a GUI), but I don't see what good it will do. You need to replace GRUB before deleting the two partitions (the smaller partition will be swap, not GRUB). There must be a way to replace the bootloader with vista - there must be.

---

### Post by Geohevy on 2008-02-18
Problem solved!

I used the excellent program EasyBCD and just rewrote the Vista MBR.

---

