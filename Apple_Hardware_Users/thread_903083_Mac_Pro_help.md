---
title: "Mac Pro help"
date: 2008-08-27
forum: Apple Hardware Users
---

### Post by bearcatrp on 2008-08-27
Been reading the posts about installing ubuntu. Been told ubuntu is one of the best linux flavors out there so am concidering installing on my mac pro. Can any mac pro users tell me:
1. Are there performance gains?
2. Do the pro's run cooler, hotter, etc..?
3. Would the 64 bit version be better than the 32 bit version?

Was thinking of pulling all my hard drives and install a clean drive, install on this, then put my leopard drives back in, use the option key a boot to pick which one I want to boot to. Will this work? or would it be better to leave my drives in (including the empty one) and boot off the install disk and install? Leopard is backed up but didn't want ubuntu screwing up my leopard disk. 
Suggestions welcomed.

---

### Post by kosumi68 on 2008-08-28
If you start off using MacOS to partition the harddrive, then install Ubuntu onto some of those partitions, you will have less problems adding back MacOS. In particular, the GPT partition tables must be in order for MacOS to work properly.

---

### Post by cyberdork33 on 2008-08-28
Installing on a second hard drive is a bit funny because of the way the Mac hardware works. There is some information here:
[http://wiki.debian.org/DebianOnIntelMacPro#line-187](http://wiki.debian.org/DebianOnIntelMacPro#line-187)

If you install to a new drive with only that drive attached, and then add another back later, it might actually work (since Ubuntu would then assume it is on the primary hard drive). I would make sure the disc is in GPT format though as I do not know the effects of mixing various partitioning types in one machine.

---

