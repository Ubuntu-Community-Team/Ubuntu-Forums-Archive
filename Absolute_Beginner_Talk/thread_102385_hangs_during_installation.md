---
title: "hangs during installation"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by randum_idiot on 2005-12-11
my computer hangs during the installation of ubuntu 5.10, it gets up to the part where the title says "detecting hardware to find CD-ROM drives" at 86% where it says "loading module 'ide-cd' for 'linux ATAPI CD-ROM"

This computer does meet all the minimum requirements...

It is not because of a scratched/bad/dirty CD

I tried it with the live CD and it does the exact same thing...

My computer is an ACER travelmate 520iT and although i doubt it makes a difference on why it hangs i have the hard disk with 2 partitions already set up (both FAT32) with the main partition (10 GB) with windows 2000 pro and the other partition (5 GB) with win98se. The last 5 GB is left for UBUNTU (un-partitioned as yet).

Sorry that I posted this in 2 forums...

---

### Post by randum_idiot on 2005-12-11
any solutions???

---

### Post by randum_idiot on 2005-12-12
^^^bump^^^
I NEED A SOLUTION AGGGHH!

---

### Post by randum_idiot on 2005-12-13
^^bump^^
HELP!

I beleive i have figured the problem to be that i need to find an appropriate cd rom driver for ubuntu...

If anyone can find a Matshita CD-ROM CR-176 driver for ubuntu, it'd be much, much appreciated!!! I have actually found out from searching a bit that this brand is actually under the name MATSUSHITA which is apparently panansonic...

Anyone that can get me a driver disk that i can use when i try installing under "expert" would be much, much appreciated!

---

### Post by chuck_2330 on 2005-12-18
Hi randum

Not sure if you got an answer to your post but I got the same error and solved it by adding the following to the boot command-

boot: linux pci=noapci

Works for me. YMMV

cheers

---

### Post by n00b on 2006-01-25
When, where and how do you insert "linux pci=noapci"

---

### Post by kaamos on 2006-01-25
When the installation cd boots, you get a screen that looks something like this: [http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=1](http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=1) (the pic is from version 5.04). So type it to this prompt.

---

### Post by n00b on 2006-01-25
ok thanks I figured that out but now I get stuck here:

> Disabling IRQ #11
irq 11: nobody cared!
Stack pointer is garbage, not printing trace
handlers:
[] (ide_intr+0x0/0x18e)
[] (ohci_irq_handler+0x0/0x80e)
[] (usb_hcd_irq+0x0/0x67)
Disabling IRQ #11 

Does nothing after that.

---

