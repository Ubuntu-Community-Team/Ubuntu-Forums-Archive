---
title: "rEFIt Problem"
date: 2010-09-30
forum: Apple Hardware Users
---

### Post by nicholaschum on 2010-09-30
Hey guys, another post from me regarding the previous post.

This time I have a different situation. I can choose Windows, and it runs Windows, but when I choose Linux, with GRUB installed on the partition (sda6) and Windows still boots.

What I have regarding this problem on Linux:
Swap Area = 2001mb
Data = 21453mb
GRUB installed on sda6, NOT MBR!

OS'es installed: Mac OS X Snow Leopard, Mac OS X Tiger, Windows 7 and Ubuntu 9.04 installed in order from OSX to Ubuntu. Advanced install - Bootloader installed to sda6

Total Partitions:
300.11GB - Macintosh HD - Snow Leopard HFS+
25GB - Macintosh HD - Tiger HFS+
150GB - Windows 7 NTFS
23GB - Ubuntu Ext3 - Beginning
2GB - UBUNTU SWAP AREA - End

Please help!

Thanks

Nicholas

---

### Post by nicholaschum on 2010-09-30
bumpity bump bump :KS

---

### Post by nicholaschum on 2010-10-02
sorry can no one help me here?

---

### Post by linuxopjemac on 2010-10-02
[http://refit.sourceforge.net/help/linux_boots_windows.html](http://refit.sourceforge.net/help/linux_boots_windows.html)

---

### Post by nicholaschum on 2010-10-02
> **linuxopjemac said:**
> [http://refit.sourceforge.net/help/linux_boots_windows.html](http://refit.sourceforge.net/help/linux_boots_windows.html)

Thanks, but I need a detailed walkthrough on how to do that. Whenever I put my Grub onto /boot partition OR my / partition, and when its installed, the next time I booted up, it says "Missing Operating System".

---

