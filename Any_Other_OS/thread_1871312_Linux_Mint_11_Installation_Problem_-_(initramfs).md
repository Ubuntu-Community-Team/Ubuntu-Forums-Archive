---
title: "Linux Mint 11 Installation Problem - (initramfs)"
date: 2011-10-28
forum: Any Other OS
---

### Post by ChildOfMana on 2011-10-28
I know this is a question about Linux Mint but as it's based on Ubuntu I thought I'd try here first rather than sign up at the Mint forums for the sake of one question.

I've recently built a new rig comprising an Intel Core i5 2500K 3.30Ghz (@ stock) in an MSI P67A-GD53 (B3) Mobo.

I've got Windows 7 sitting nice and happy on a 320Gb SATA HDD and I've got two WD 1.5Tb SATA HDDs for Linux (I have large data needs!!!). The plan was to use the Win7 installation for gaming (what else!) and Linux for everything else. I've been using Linux in one form or another on a few different rigs for a number of years now without any problems whatsoever (including Mint 11).

Trying to install Mint 11 this time around however throws up the following error then drops to a BusyBox shell:

```
(initramfs)Unable to find a medium containing a live file system
```

It refuses to go any further. I tried installing the 64-bit DVD and have also tried using a verified working 32-bit CD but the same thing occurs. I did a little digging on Google and tried switching the SATA controller from IDE mode to AHCI mode in the EFI. This solved the problem and the live CD (and DVD - I tried both) now makes it all the way to the desktop. I'm assuming installing it shouldn't be a problem from here but I don't know yet as I haven't tried as I wanted to test Win7's reaction to the change in SATA mode first and - just as I thought - it didn't like it! It refused to boot and I had to switch back to IDE mode to get it to play nice again.

I didn't originally use AHCI mode when I installed Windows as I couldn't be bothered messing around with drivers etc and as I don't need to hot swap the drives I didn't think it mattered.

The problem I've got now is - how do I install Mint whilst keeping the SATA controller in IDE mode so I can also use my Windows install? Any suggestions?

I've read that booting from a Live USB might work but UNetbootin only supports Mint 10 or lower and I really need 11 on there!

Thanks in advance!

---

