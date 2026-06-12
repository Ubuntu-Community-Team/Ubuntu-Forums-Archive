---
title: "XP in Vmware? On a g4"
date: 2008-06-01
forum: Apple Hardware Users
---

### Post by ruialexbarbosa on 2008-06-01
Strange question for an apple forum I know, but is it possible (and easy) to install XP with VMware in a G4 powerbook?

---

### Post by yoasif on 2008-06-01
no, you need a hardware emulator, like QEMU.

---

### Post by ruialexbarbosa on 2008-06-01
Is it worth it? Or might as well forget it? I would want to have photoshop and lightroom, but it's probably best to just do a dual boot with mac osx and ubuntu... What do you think? Or put osx in vmware?

---

### Post by frog_pilot on 2008-06-01
> **ruialexbarbosa said:**
> Strange question for an apple forum I know, but is it possible (and easy) to install XP with VMware in a G4 powerbook?  I would want to have photoshop and lightroom
really strange thinking... :)

AFAIK there is no vmware port for ppc linux.
To run OSX inside ubuntu there is MOL, but I only tested it for feisty (7.04). And it isnt running (yet) on hardy.

You can emulate a x86PC with qemu and run windows on it. But forget about any of the adobe cs progs. I think they wont start at all, or at least take hours to open...

Take gimp and fspot... For most usual tasks it will suffice

Or contact your adobe support and try to change your licence to OSX-Adobe CS.

---

### Post by ruialexbarbosa on 2008-06-01
Maybe the best would be to dual boot? Lightroom is a must.

---

### Post by frog_pilot on 2008-06-01
Dual boot is no problem. And if you want to use lightroom in OSX, it is suggested :)
If you have osx already installed, ubuntu will install itself as dual boot by default.

---

### Post by ruialexbarbosa on 2008-06-01
Thanks,

but how do I find space for ubuntu? As far as I understood, OS X runs on HFS+, I need to create partitions for Ubuntu. I would like to split my 60gb in 2, use mainly Ubuntu, but open OS X once in a while.

Should I just pop the live ubuntu cd in and start partitioning with gparted, or is there more to it?

I'm used to (on a pc) having 4 partitions

1 -Fat32 for Windows
2 - Fat32 for windows + ubuntu documents
3 - Ext3 for Ubuntu
4 - Swap

Should I make a different partition for documents? If yes, in which format?

Thanks

---

