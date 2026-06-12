---
title: "SD card in reader - how should Ubuntu handle it?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-04-30
If I plug in a card reader, then put an SD card in a slot, Ubuntu sees it as I see the access light flash, and dmesg reports it as sdf1.

I can manually mount it from a command line, but I was expecting Ubuntu to pop up some GUI dialog box (like it does when I plug in my camera).  Surely new users aren't expected to have to 'sudo mount /dev/sdf1 /mnt/tmp' or similar from a command line?

---

### Post by mattmole on 2007-04-30
Hi,

That is weird. On my machine it just automounts and asks if I want to import images. If I select no then I can just get into the directory structure from the desktop.

Sorry I havent anything more than that to say!

---

### Post by ubnewbie2 on 2007-04-30
> **mattmole said:**
> Hi,

That is weird. On my machine it just automounts and asks if I want to import images. If I select no then I can just get into the directory structure from the desktop.

Sorry I havent anything more than that to say!

Yep, all it does is report this in dmesg
```

[ 9885.714282] SCSI device sdf: 2012160 512-byte hdwr sectors (1030 MB)
[ 9885.716401] sdf: Write Protect is off
[ 9885.716405] sdf: Mode Sense: 03 00 00 00
[ 9885.716408] sdf: assuming drive cache: write through
[ 9885.720146] SCSI device sdf: 2012160 512-byte hdwr sectors (1030 MB)
[ 9885.722277] sdf: Write Protect is off
[ 9885.722283] sdf: Mode Sense: 03 00 00 00
[ 9885.722286] sdf: assuming drive cache: write through
[ 9885.722538]  sdf: sdf1
```

---

### Post by mattmole on 2007-04-30
Very bizarre. Try reporting it as a bug!
[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

---

### Post by ubnewbie2 on 2007-05-01
I have reported it as a bug.  I just discovered tonight that SOME cards, like the one from my camera, get recognised as photo cards, but this one, from my Palm PDA, is ignored, even though it has some photos on it from being in my camera as well.  Maybe they have to be formatted by the camera?  Still, ubuntu should recognise a plain memory card anyway.

---

