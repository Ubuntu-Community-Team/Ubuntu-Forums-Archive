---
title: "Linux on an iMac G5 1.9Ghz?"
date: 2010-09-16
forum: Apple Hardware Users
---

### Post by al.adab on 2010-09-16
have acquired an Apple iMac G5 1.9Ghz iSighs as a second computer and was wondering if it's possible to replace the Mac OS X (Leopard 10.5) with a Linux distro, preferably Ubuntu...

...a Google search as in this respect proven to be quite discouraging...any idea? I'd rather not to go for a dual boot, if that's feasible...

thanks!

---

### Post by linuxopjemac on 2010-09-16
You can install Lucid Lynx. The fans problem can be solved by adding therm_pm72 to /etc/modules.

---

### Post by jadedcritic on 2010-09-16
Seconded.  I've got ubuntu running comfortably on my imac, although my imac is an intel I'm comfortable in claiming that it's not much faster then 2GHz.

I did have some...issues.
offhand, the boot camp bootloader thinks its windows, which is a largely trivial, just cosmetic thing, but boot camp loads first, then grub.

The linux installer, unity I think they call it?  Wouldn't help me resize my snow leopard partition, which is largely to be expected.  I ended having to play three card monte with partitions to free up half the disk space for linux.

It's been pretty painless in terms of drivers, what's making me crazy is the filesystems.  10.6 reads and writes in HFS and FAT, and linux will write in just about anything, save HFS, but as it turns out there are packages in the Ubuntu repository that will let it read HFS.  (HFSUtils & HFStools)  I'm sliding slowly over, doing more in the linux part and less in the OSX.  Eventually I'd like to nuke it completely, but I think I have too many apple devices around the house to not have itunes.

---

### Post by al.adab on 2010-09-20
thanks for your advice :) 

has anyone tried Yellow Dog Linux by any chance?

[http://www.yellowdoglinux.com/support/installation/ydl6.2_apple_guide.pdf](http://www.yellowdoglinux.com/support/installation/ydl6.2_apple_guide.pdf)

---

### Post by chatwebcam on 2010-09-21
thanks !

---

