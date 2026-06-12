---
title: "How to install Win7 &amp; Ubuntu on a Macbook WITHOUT OS X?"
date: 2010-07-12
forum: Apple Hardware Users
---

### Post by Jheric on 2010-07-12
I want to install Windows 7 on my Macbook and dual boot with Ubuntu. **But I want a completely OS X free system. Is there a guide for doing this?**

The biggest problem I see with it is *not losing my EFI partition* in case I wish to reinstall OS X later.

How can I go about doing this?

---

### Post by Jheric on 2010-07-12
Could I just do a complete wipe and use GRUB as my bootloader? And then reinstall EFI if I ever decide to go back to OS X? Or am I SOL if I want to recreate the EFI later?

---

### Post by Legal Beagle on 2010-07-12
I would seriously consider getting a fresh install of Mac OSX and an external hard drive, and cloning it sector-by-sector with CompuApps Drive Wizard 
[http://store.compuapps.com/codrformacos1.html](http://store.compuapps.com/codrformacos1.html).

Then, I would install Ubuntu and dual-boot Windows 7 using GRUB as my bootloader just as if it were any other box.

If you decide you want OSX again and you completely messed up your disk, you can boot your mac in target disk mode and use another computer to copy your sector-by-sector cloned disk back onto the Mac to have the clean install of Mac OSX you started with.

Or, you could always make sure the external hard drive is the same type as your Macbook in an enclosure and just do a little "brain transplant" to take it out of the enclosure and into the Macbook.

---

### Post by manoj11 on 2010-07-13
Is Windows 7 is more Faster than Vista, previously i had Vista Home as ships with my laptop and I had a very bad experience with that one and I thought that i should removed this one and I Installed a Windows XP.

So Could you please let me know shall It will worthly upgrade?
I have a Laptop Core2Duo with 3GB of RAM. 


___________________________________-


  [panic   attacks](http://www.panicattackspace.com/) [Rachael Ray](http://www.medpro2006.com)

---

### Post by Jheric on 2010-07-13
I think that, if I want to be safe, I'll need to tripleboot. Apparently I can't run OS X on less than 18.5gb... jeez... sucker is huge!

Because of how much space each OS takes up though, and the fact that I can share drive space between them, effectively, unless it's FAT32 and I'm will to deal with file handling annoyances, I'm thinking that running a pure Win7/Linux machine is impractical. I should probably just stick to OS X/Win7 for space reasons.

/depressed.


@manojj11 - I'm assuming you're an Apple user? If so, I can tell you that I've already run windows 7 on my Macbook before and it runs perfectly fine. Just make sure to install the bootcamp software for it to make all your hardware work properly. There were no speed issues when I was running it.

---

