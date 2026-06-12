---
title: "How can I get Ubuntu 6.06.1 to boot with no monitor connected?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by nrundle on 2007-05-15
I just installed Ubuntu 6.06.1-Server and am having video problems with console.  The video card in this system is a S3 Trio.  The system will not boot with my old (Compaq) monitor and this video card, but will boot with old monitor and ATI Radeon 9600 video card.  Also, the system will boot with Sony Trinitron monitor and S3 video card.  Why does the video card/monitor affect the boot up?

What I need to be able to do is boot the system with no monitor connected.  I run this as a web server and ssh to control anyway.  I tried booting with the S3 video card with no monitor connected and, after say 10 minutes, tried to ssh but could not connect.  Then I connected the video cable of the monitor to the system and I heard the hard drive resume booting and then I could ssh in.

Now I need this monitor for my other desktop system so I cannot have it connected just to boot.  How can I force Ubuntu to boot with no monitor connected?

-Nick

---

### Post by oilchangeguy on 2007-05-15
is the card pci, or on the motherboard? if it's pci, just remove the card, on board, disable it in the bios.

---

### Post by nrundle on 2007-05-15
Yes it is a PCI card.  I suppose I can remove the card, but this seems like a temporary solution.  I guess it doesn't make sense to me why the system fails to boot with no monitor connected to the card.  I'm wondering where the problem lies? Kernel? Grub?  I already have the BIOS set to halt on no errors so it will attempt to boot no matter what.  Could Grub, or the Kernel be requesting monitor information through the BIOS and receiving an unhandled error?

EDIT: Removing the Video card entirely DOES allow the system to boot up and I CAN ssh into now.  Temporary solution works, thanks.  Now I need to figure out how to make the S3 Trio video card work with the old Compaq monitor so that I can get console access in the event of networking failure.  I suppose I could always upgrade one or the other but why buy new stuff when the old stuff still works?

---

