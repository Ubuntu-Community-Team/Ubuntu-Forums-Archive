---
title: "LiveCD won't boot from USB optical-drive"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by darrelljon on 2008-03-29
My LiveCD won't boot (completely to a desktop) from my USB optical disc drive (DVD-RW) attached to my laptop. Well, it will boot, but stops during the boot. I get an error about initramfs. I tried Puppy Linux (which loads itself to ram) and it booted live to a usable desktop okay. I could try Ubuntu and copy2ram but the laptop only has 512Mb RAM.

---

### Post by jken146 on 2008-03-29
That should be enough RAM.  Give it a go.  It'll be a little slow though -- if you're installing you mught want to just go with the alternate CD.

---

### Post by rkd on 2008-03-29
Perhaps the Live CD had some errors when it was written.

It might be a good idea to choose the "Check CD for defects" option on the menu that comes up when booting from the Live CD.  If that check finds problems, then check the MD5 checksum on the .iso file you downloaded. If the MD5 is bad, download again and recheck the MD5 before burning the disk.  If the MD5 is okay, just reburn the Live CD.  Make sure you choose a moderate burning speed -- burning at top speed seems to cause bad disks for many people.

---

