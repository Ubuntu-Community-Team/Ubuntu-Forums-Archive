---
title: "computer not booting"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by borner on 2008-04-02
Hi, not sure if this is in the correct section so sorry in advance if it is not. I recently bought a second hard drive for my computer onto which i installed ubuntu, i have windows vista on my first hard drive. I partitioned the drive in half, half for ubuntu, half for some extra memory for windows. It was all working fine until yesterday, whilst i was using windows the computer crashed. I rebooted and after a few minutes this it crashed again. After this happeneing several times i noticed the seond hard drive was dissapearing from my computer in windows. Now when i turn the computer on i get a message saying error 21 cannot load grub. Im assuming the second hard drive has stopped working properly and the grub now cannot load from it, so now i can nither load windows or ubuntu. I have no idea where to go from here, does anyone have any ideas how to resolve this?

---

### Post by Crafty Kisses on 2008-04-02
You might want to look into [SuperGRUB.]("http://supergrub.forjamari.linex.org/")

---

### Post by owenll on 2008-04-02
Does this help?

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by borner on 2008-04-02
thanks for the replies, that thread does help but even if i get the grub wroking ubuntu is still on the hard drive that is not working, im clueless as to why it has suddenly stopped functioning properly, is it most likley to be a driver problem for a hardware problem?

---

### Post by Crafty Kisses on 2008-04-02
When Windows was crashing, were the crashes one right after another?

---

### Post by borner on 2008-04-02
windows would work fine for a while then the drive would dissapear and the computer would crash, then if i turned it off and left not a minute or two it it would boot ok then it would happen again after half an hour or so of windows being used. Now i cannot get it to boot at all, it gives the error message every time.

---

### Post by Daveg4otu on 2008-04-02
Could be the drive itself - check it is showing inthe BIOS and also d/l and run the drive manufacturers  diagnostic  software(From either a floppy or bootable CD)

---

### Post by Crafty Kisses on 2008-04-02
> **Daveg4otu said:**
> Could be the drive itself - check it is showing inthe BIOS and also d/l and run the drive manufacturers  diagnostic  software(From either a floppy or bootable CD)
Yeah that's what I was thinking, your drive might possibly be failing for some reasoon.

---

### Post by borner on 2008-04-02
yeah the drive does not appear in the bios. One other thing i noticed is after the drive dissapeared widows came up with a message saying it was installing drivers for the drive before it crased, dont know if that would point more towards a driver problem?

---

### Post by Crafty Kisses on 2008-04-02
> **borner said:**
> yeah the drive does not appear in the bios. One other thing i noticed is after the drive dissapeared widows came up with a message saying it was installing drivers for the drive before it crased, dont know if that would point more towards a driver problem?

Have you checked the drive to see if anything got disconnected or loose?

---

### Post by borner on 2008-04-02
yeah that was my first check, all the cables are connected securley

---

### Post by Crafty Kisses on 2008-04-02
> **borner said:**
> yeah that was my first check, all the cables are connected securley

Sorry if you already answered this but what kind of drive do you have?

---

### Post by borner on 2008-04-02
this is its spec 'Samsung SpinPoint T166 500GB 7200RPM SATA 3GB/s 16MB Cache'

---

### Post by Daveg4otu on 2008-04-04
If the drive is not showing in the BIOS then it's a good bet that the problem is hardware rather than software - try using different SATA connecter cables and a different power connecter from the PSU.

---

