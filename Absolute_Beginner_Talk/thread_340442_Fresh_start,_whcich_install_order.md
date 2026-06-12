---
title: "Fresh start, whcich install order"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Neoito on 2007-01-17
I'm just about to get a new hard drive and will be installing Windows and Ubuntu, is there one way round to do this that is better than the other, ie: Ubuntu first then partition then Windows, as I suspect?

---

### Post by ThrobbingBrain66 on 2007-01-17
Installing Windows first is the better option.  If you were to install Ubuntu first and then Windows, GRUB gets over-written and then you have to go through a whole process of reinstalling it.  It's much easier to install Windows first.

---

### Post by milton1 on 2007-01-17
Windows first. Otherwise the windows installs screws grub and you have to reinstall the bootloader.

---

### Post by thornomad on 2007-01-17
If you wanted, you could run the Live CD first, partition the Hard Drives to your liking (maybe one NTFS for Windows, a FAT32 for Shared Documents, then your two EXT3 partitions for your "/" root and swap areas) ... then, I believe it worked for me, you could exit, install windows to the NTFS partition (it won't recognize the EXT3), and afterward, do the Ubuntu install.

But resizing a full winXP partition works too.

---

### Post by Neoito on 2007-01-18
Thanks guys, the above seems perfect but I'll probably just go for the simpler Windows first approach.

---

### Post by j19sch on 2007-01-18
> **thornomad said:**
> But resizing a full winXP partition works too.
You can manually create the Windows partitions during install. Saves you the trouble of resizing.

---

### Post by Neoito on 2007-01-19
This is all great guys, thanks.

While we're here, what partition sizes would you recommend?

The XP install will only be used for a distance learning call I'm doing, so I only "need" around 4/5gb of space. I'm thinking of giving it a 15/20gb partition just to be safe.

The Ubuntu install will be used for absolutely everything else.

120gb hdd by the way.

---

### Post by bries on 2007-01-19
> **thornomad said:**
> If you wanted, you could run the Live CD first, partition the Hard Drives to your liking (maybe one NTFS for Windows, a FAT32 for Shared Documents, then your two EXT3 partitions for your "/" root and swap areas) ... then, I believe it worked for me, you could exit, install windows to the NTFS partition (it won't recognize the EXT3), and afterward, do the Ubuntu install.

But resizing a full winXP partition works too.
Could you direct me to a good and straightforward HOWTO regarding using the Live CD and creating partitions?

---

