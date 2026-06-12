---
title: "Installation deleted my partition"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by indijay on 2006-07-08
Hello All,

Yesterday night, I tried to install Ubuntu on my partitioned HDD (35GB with windows, 30GB for linux and rest as data drive)
During installation, I asked root drive as the 30GB drive and swap drive as the data drive) but for some reason, it gave me error that the disc contains uncorrected errors and it can't continue.

I don't kow if this is because the disc is NTFS formatted. Now today morning when I boot my machine in windows as usual, I don't see this data partition anymore. (Also, I must mention, I couldn't mount any of these drive through live CD and I have no idea why so)

Any idea how do I get it back?

Many thanks

---

### Post by Daiver on 2006-07-08
If I read correctly, you set the whole data partition to use as swap?

If you did, the installer formatted entirely to use as swap.  I don't want to be an alarmist, but if this is the case, probably all your data is gone and Windows can't read swap partitions, which is why it's not showing up.

I'm quite a new Linux user, so this may not be entirely correct.

---

### Post by indijay on 2006-07-08
Daiver,

Thanks for your reply

In fact, it only made that NTFS partition as linux swap so may I say it just changed the ststus of that partition, everything is there. I recovered it using Acronis Disc Director and had to restart machine to see it in explorer.

---

