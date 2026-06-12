---
title: "Cant See My Partition!"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by J2A. on 2007-08-29
Here's the prob,

I made a partition of my drive and formatted as ext3, before wen it was FAT32 I could see it with all the other drives/partitions when I went to Places > Computer.

Now this partition is completely invisible, I cant see it at all!

When I go to GParted I can view it as normal, format it etc, but after than it vanishes!

I've tried deleting it, formatting it again, formatting as FAT32 again, and various other stuff but it just doesn't show :(

Plz hellp, thnks *thumbs up*

---

### Post by benerivo on 2007-08-29
You may need to change the entry for this drive that is in your /etc/fstab file. Open this file to see if the entry still reads vfat. If it does, then you can try changing it to ext3. Then reboot and see what happens.

---

