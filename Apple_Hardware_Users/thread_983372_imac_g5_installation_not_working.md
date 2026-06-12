---
title: "imac g5 installation not working"
date: 2008-11-15
forum: Apple Hardware Users
---

### Post by Zopiac on 2008-11-15
My friend has an iMac G5 with Leopard, used boot camp to install Windows, and we used the Ubuntu 8.04 LiveCD to repartition the hard drive (took 5gb or so out of the mac partition) and installed ubuntu to it. However, when i booted up the comp, it said there were no bootable devices! im not sure what to do now. i can boot from the livecd, though, but not any of the three partitions on the HDD

---

### Post by tiresia on 2008-11-15
> **Zopiac said:**
> My friend has an iMac G5 with Leopard, used boot camp to install Windows
Are you sure, that it is an iMac G5, a PowerMac? On powerpc you can't use boot camp

---

### Post by Frak on 2008-11-15
G5 is a PowerMac machine, running a PowerPC G5 processor. Bootcamp ONLY runs on the Intel Mac Pro's and Intel iMac's. If you indeed have a PowerMac, you need VirtualPC for Mac instead.

---

### Post by Zopiac on 2008-11-15
It's an aluminum one; Intel

---

### Post by Frak on 2008-11-15
> **Zopiac said:**
> It's an aluminum one; Intel
OK

Good to know. Your GUID table is probably out of order and needs to be resynced with rEFIt. Other than that, you could try the ole' hold option on startup trick, so you may see if it can find a volume to boot from.

Oh, G5's and Intel Mac Pro's are both Aluminum cased.

---

### Post by Zopiac on 2008-11-15
how do install rEFIT onto it when i cant even boot into it?

---

### Post by Frak on 2008-11-15
[Burn a rEFIt disc]("http://refit.sourceforge.net/doc/c1s5_burning.html") and boot with it by holding the C key after your mac has given the gong confirmation.

---

### Post by Zopiac on 2008-11-15
in order to burn a rEFIT disk i need a program for windows to burn a .cdr file. I cant find one; what is a program to do this, or is there a .iso file to download?

---

### Post by Frak on 2008-11-15
.cdr is just a .iso with a different name. Just change .cdr to .iso.

---

### Post by cyberdork33 on 2008-11-16
you can also install to a USB stick if you like.

Please use the information in the "Before You Post" link to determine your Mac version properly and to find the appropriate documentation for your Mac. You should also check the FAQ stickied at the top of the forum as there is a item specifically about this. (and would have easily been found by searching as well)...

[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

