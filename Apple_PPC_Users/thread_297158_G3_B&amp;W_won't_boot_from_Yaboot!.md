---
title: "G3 B&amp;W won't boot from Yaboot!"
date: 2006-11-10
forum: Apple PPC Users
---

### Post by ThreeDee912 on 2006-11-10
I'm a new Ubuntu user who just finished installing 6.10 Edgy on my old PPC B&W G3 (it's new world). When I clicked restart, it eject the disk, etc. When I press return to restart, nothing happens! I waited a few mins, thinking it might be doing something. Nothing. I couldn't do anything else, so I forced a hard restart.

Now, whenever I startup, I get a message that yaboot "Can't open device /pci@80000000/pci-bridge@d/pci-ata@1/@0/disk@1:0" and that it can't open the config file, followed by a "Unable to open file, Invalid device"

Then it leaves me at a 'boot:' prompt. I've tried a bunch of things, read the 'help', and still can't figure out what is wrong.

I tried erasing the partitions, and installing again, but it still does not boot.

I can still boot into OS X though.

I also have 2 HD's, one old 12GB one and a 80GB one. I partitioned the 80GB one in half, one part HFS+, one part free space, and let the ubuntu installer partition the free space.

---

### Post by ThreeDee912 on 2006-11-12
Tried reinstalling, no go. Maybe I should just reset the NVRAM and forget about it?

---

### Post by sleestak on 2006-11-13
You arent, by chance, using scsi drives?

---

### Post by ThreeDee912 on 2006-11-13
Nope, no SCSI drives. Just ATA.

---

### Post by sleestak on 2006-11-13
I am guessing the 12gb drive is the one that came with it? Did you just add the 80g to it?

---

### Post by Apatride68 on 2006-11-13
Exactly the same problem ! Same machine with 1 Gb RAM - Tried to add PCI SATA Card with new 80Gb HD, but Sil3112 not recognised...previous version of Ubuntu worked fine ! (though never tried it with SATA setup)

---

### Post by TheWalt on 2006-11-13
I just went through this exact same thing.  When you get to the part of the install process which partitions the hard drive make sure you choose the "with LVM" option.  At least that is what fixed it for me.

---

### Post by ThreeDee912 on 2006-11-15
> **sleestak said:**
> I am guessing the 12gb drive is the one that came with it? Did you just add the 80g to it?

Yep. The old 12GB came with the G3, the 80g is new new one.

80 GB is partitioned on half, one HFS+ (plus whatever Apple adds in), other half has whatever the Ubuntu installer did to it.

The 12g is left as it is just to hold some extra files and as a spare backup HD, although it is a bit old.

---

