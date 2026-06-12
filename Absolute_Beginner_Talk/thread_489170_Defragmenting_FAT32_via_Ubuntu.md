---
title: "Defragmenting FAT32 via Ubuntu?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Sabretooth on 2007-07-01
Okay, here's the situation. I have two drives - one 10GB and the other 80GB. My 80 has Windows XP, which I am happy with. The 10 has Ubuntu. I had Windows ME on the 10, which got corrupted and had to be formatted.

Now, I'm using a family computer and Dad has his say in things. He doesn't trust a lot of non-Microsoft stuff of Windows, and hence will not allow a non-Microsoft application to defragment Windows. The Windows ME Defrag was very efficient, and would complete within hours (both drives, mind you!). But the Windows XP Defrag is insanely slow and can take upto a full day sometimes.

Now, I'm not switching to Ubuntu completely which means I still have to do housework on Windows XP. So, I was wondering, is there any package that allows defragmenting FAT32 drives in Ubuntu? And is it good?

---

### Post by spin2cool on 2007-07-01
To the best of my knowledge, there is no non-windows way to defrag a FAT32 drive.  I spent quite a while looking for the solution before finally giving up. 

Why not convert the drive to NTFS?  It doesn't have the same fragmentation problems, and there's good ntfs support out for linux these days.  It's better for windows anyway.

---

### Post by Sabretooth on 2007-07-01
Well, to convert it, I'm guessing I'd have to format it? Sorry, not exactly wanting to format it. Too much data to backup. Besides, it fine anyways. But I'll keep it mind next time I have to format it.

---

### Post by prince_niceguy on 2007-07-02
> **Sabretooth said:**
> Well, to convert it, I'm guessing I'd have to format it? Sorry, not exactly wanting to format it. Too much data to backup. Besides, it fine anyways. But I'll keep it mind next time I have to format it.

you can use convert command to convert the fat disk to ntfs. there is no need to format it.

---

