---
title: "Install on PBG4 with no DVD -- from HDD only"
date: 2009-05-02
forum: Apple Hardware Users
---

### Post by mingtien on 2009-05-02
Okay here's a bit of a challenge, if anyone can think of a workaround, I would be very grateful!

I've got a PowerBook G4 (12") which died on me in January: something corrupted the HD so it would no longer boot, and the Superdrive will not boot anything (tried Mac OS, various Mac Linux, and some rescue CD's).  I am able to boot in safe mode and see data, but as it will not boot from CD, I've no way to recover the OS.  I have a lot of useful data on it, and it would be very useful if I can get any OS (preferably Ubuntu) running on it.

In the interim, I've been using a borrowed PC notebook, on which I am currently running Ubuntu 9.04 (Jaunty, and it's great!).

I'm out 'in the field' with no option to purchase any additional hardware, and no other Macs around (otherwise I would just boot as a firewire target and go that way around, at least for data retrieval).

I'm wondering if it would be somehow possible to:

1.  Install a Ubuntu for PowerPC boot image onto a portable HDD I have (1 TB LaCie drive, that does both Firewire and USB 2.0)

2.  Boot the Mac from that drive, mount the internal drive, write the data to another partition on the external drive, then proceed to install Ubuntu on it.

If someone can think of any way to do this, then which is the best version of Jaunty to run on an old PowerBook?  I've been using garden variety Jaunty, and have been *very* pleased with it to date.

Thanks very much in advance for any advice!!!

---

### Post by stream303 on 2009-05-02
> **mingtien said:**
> 1.  Install a Ubuntu for PowerPC boot image onto a portable HDD I have (1 TB LaCie drive, that does both Firewire and USB 2.0)

That would work great since all you have to do is hold down the alt/option key to be able to boot from a firewire external drive - but getting the image on there in the first place since you are out in the field is the hard part. :)

Is there anyone out in your field that has access to a firewire-capable external cdrom drive?  If so, the alt/option key would solve that issue again.

I wish I had an answer - it would be a very interesting thing to see if there would be some way you could just attach a firewire cable between the powerbook and another machine with firewire, boot with the alt/option key and do it that way, akin to target disk mode.

I wish I had another firewire-capable box to know this myself...

---

### Post by tiresia on 2009-05-02
I'm afraid that you can't install Ubuntu from the Firewire/USB HD - if you don't have a second PowerPC running Linux.
The problem is not to boot from an external Firewire/USB HD - as stream says, you would just need to press the OPT-Key at start up (but you should have also an alias 'fw' in Open Firmware aliases), but to make this Firewire/USB HD bootable.
To make it bootable, you need to format it with mac-fdisk - that you don't find on a x86 Ubuntu (Debian) System.

You have three solutions:
1. Find a second powerpc mac and following this how-to mac you external HD bootable
[https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld](https://help.ubuntu.com/7.04/installation-guide/powerpc/ch05s01.html#boot-newworld)
2. Boot the ubuntu kernel with TFTP - you find some infos in the same link
Of course this is not very easy if you are not experienced with Linux on PowerPC
3. Find a working CD-ROM and install it in your PowerBook

---
Maybe, before doing any attempt to install linux, you should recover your data on the internal HD. The easiest solution here again is to install a working CD-ROM or just to plug the internal HD in another PC running Ubuntu and to copy all your important files.

Last consideration. Are you sure that your CD-ROM is broken? Have you tried to zap PRAM (pressing ctrl-opt-P-R at bootup)?

---

### Post by mingtien on 2009-05-02
HI Folks,

Some really great suggestions (thank you!)

I think the easiest thing will be to try to find an external DVD/CD drive, and work from there.

I've tried zapping the proms, and that did not work.

I guess what I was hoping to find was -- some way to download a bootable image of Linux for  PowerPC and, using an i386 instance of Linux, some way to sort of dd that image to the external hard drive and tell it that it's bootable.

In theory this should be possible -- after all, we can certainly make an external disk bootable with Linux i386 for itself, so why not substitute the boot image at the last minute -- but it *boggles* the mind as to how one might actually go about it.

I'm thinking along the lines of: 

1. Get the disk and its 4 partitions recognised by Parted (I used fdisk and mkfs, as parted didn't seem to like a big drive like that -- after Parted refused to see the new partitions, even after I had formatted them and mounted one of them)

2. Use dd  to write the iso image to the first partition (yes, it's a waste of 200 GB, but we can clean that up after)

3. Boot from the external drive, grab data from the Mac's HD and put it onto another partition of the external drive

4. Run install -- from the external drive, now writing a clean Linux installation to the PowerPC

5. Once I am re-booted in Linux on the PPC, wipe out the booting partition on the external drive, and install Linux for PowerPC on it, making it a proper bootable drive (for emergencies), using the remainder of the 200 GB partition as my backups partition

If there is any way to do that, it would be great -- failing that, I will wait until I can get hold of a DVD drive (hmm... would a USB DVD drive work?)

Failing all of that: what if I wrote the Linux for PPC image to a 4 GB USB stick -- is there any way I could use that?

Cheers,

David

---

### Post by mingtien on 2009-05-05
Bumping this up in hopes that someone, coming back from the bank holidays, might have some further insight...

---

### Post by mingtien on 2009-05-13
I've managed to boot the PowerBook in target mode, and have recovered all the data off of it (yay!), so now it is a perfect target for experimentation :)

Booting in Target mode, I can see an OSX boot partition, and the normal MacOS partition.

Is there any way that I can somehow dd an image to the boot partition directly?

Cheers!

---

