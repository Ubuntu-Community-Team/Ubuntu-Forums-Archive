---
title: "USB Device names"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by ushills on 2007-04-04
USB Device names

I have  a number of USB flash drives that I connect to Ubuntu for various reasons.

These all mount as USBDisk, USBDisk-1, etc.  As I sync these drives using Unison, is there anyway of making their names unique, i.e. Cruzer, MMC, etc so that their path becomes sticky and I can attach them in any order.  I still want them to automount.

This way if I sync I will not get conflicts or overwritten data.

---

### Post by toscy on 2007-04-04
Well I'm new to all of this too but what worked for me was going into computer first, then right clicking properties. I could then change the name in the name box and it's kept it's name since.

---

### Post by mahiyar on 2007-04-04
In linux there are different commands like e2label , tune2fs -L, both are for ext 2/3 file system only. If you have FAT USB disk I guess the best option would be to go in windows and change using Control Panel > Administrative Tools > Computer management. Or even in linux when creating a new file system on the USB fior the first time you can give thr label in the makefs. command itself.

---

### Post by LaRoza on 2007-04-04
I have three flash drives (FAT32) and I named them in Windows long ago and the names stuck.

---

