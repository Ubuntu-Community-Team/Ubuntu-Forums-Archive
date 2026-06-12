---
title: "Powerbook G4 (PPC): Cannot boot from disc to install"
date: 2010-02-12
forum: Apple Hardware Users
---

### Post by pc_michael on 2010-02-12
Hi!

My system, Powerbook G4 circa 2005,  does not seem to recognize the Ubuntu 9.10 PPC LiveCD as bootable.

I downloaded and burned the ISO from the Ubuntu PPC site, but the Powerbook will not boot from the CD.  Methods for booting I have tried include holding C during boot, holding Cmd+Optn+Ctrl+Del, and holding Option.

When I hold option, it loads the boot menu thing, and my hard disk shows up along with an icon with the Ubuntu disc, but when I select the Ubuntu disc to boot from, the screen flickers and returns to the boot menu.

I have also tried loading Mac OS X and going to the Startup Disk control panel, but the disc does not appear as an option to startup from.  (I should mention the disc DOES mount and is accessible via Finder, so it's not like it's unreadable.)

As a "control" for this test, my Leopard disc boots fine and shows up in the all the boot menus.

As for the Linux discs, I have tried the 9.10 live disc, the 9.10 minidisc, and the 9.04 disc all from the PPC website---none of them will work.

What else can I try?

---

### Post by linuxopjemac on 2010-02-13
check the md5sum of the iso you downloaded. You should also try to burn the iso at a lower speed from disk utility.

[http://mac.linux.be/content/cd-burning-tips-iso-images-especially-slow-machines-0](http://mac.linux.be/content/cd-burning-tips-iso-images-especially-slow-machines-0)

---

### Post by pc_michael on 2010-02-13
Thanks for the reply!

I tried making a USB stick (eliminating any burn speed problems) and that didn't boot either.  So I dug out my even older iBook G4 and it boots absolutely fine from the CD.  (I was going to install it to the Powerbook via Target Disk Mode, but then I read that it confuses the bootloader.)

So I guess I can confirm that everything's fine on the Linux disc side of things, it must be my Powerbook.

I'll pursue this further in a Mac forum, buuut I'm really close to just giving up. :?

---

### Post by pc_michael on 2010-02-14
Wooo, I figured it out by myself!  It was indeed my computer's configuration, nothing to do with the Linux disc.  Here's my situation for anyone who stumbled upon something similar.

The  problem is that my firmware's **cd** devalias was set to a target other than where my optical drive actually resides.  I figured this out because, booting in to Open Firmware, "eject cd" didn't work.  So I used the **devalias** command to list all the aliases, and I went down the list typing **eject [alias]** until my disk physically ejected.  This turned out to be alias **ide1**.

So then I used **devalias ide1** to list the path to the drive, and finally **devalias cd [path to drive]** to redefine the 'cd' alias to point to the optical drive.

From there I reinserted the Linux install disk and typed **boot cd:,\\:tbxi** to finally boot into Linux and install.

Hopefully this will help somebody some day!

---

### Post by svtguy88 on 2010-02-15
That is very interesting.  I wonder how that got mixed up?  It seems like something must have happened if even control via open firmware wasn't working (eject cd).

---

