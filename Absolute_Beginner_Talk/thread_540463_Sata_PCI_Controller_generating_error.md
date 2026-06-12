---
title: "Sata PCI Controller generating error"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by mohnkern on 2007-09-01
I have been running ubuntu on a machine for the last 7 months, and today I plugged in a Sata PCI controller (Syba PCI Serial ATA Host ControllerCard) and plugged in a Seagate Barracuda 7200 hard drive).

When I start up the machine, during the kernel load (after grub) I get the following error: 

28.407615 PCI: device 0000:00:0d0 has unknown header type 7f

When I finish the boot, an fdisk -l doesn't show the new drive, and an lspci doesn't show the controller card.


Anyone have any ideas what the error means, and how to fix it?  Maybe I've got a Sata controller card that is incompatible with the Kernel?

---

### Post by nonewmsgs on 2007-09-01
i have had badluck with pci sata cards even after the drives are detected with linux and windows, but i wish you the best of luck with that.

---

### Post by mohnkern on 2007-09-01
Problem has been solved by unplugging the card, moving it into slot 0 and removing a SB Live Card.

---

