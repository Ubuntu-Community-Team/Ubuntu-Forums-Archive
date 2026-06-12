---
title: "mkfs question."
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-07-21
I got an SD card here with pictures on it I don't want to lose, yet I think the file system got corrupt cause it prompts me about formatting it in order to use the card.

If I do a mkfs on the card, will that format it? Or just create the FS and leave the files intact?

---

### Post by p_quarles on 2007-07-21
Yes, mkfs will definitely format the card and delete everything. If you have access to a Windows or Mac machine, you might try rescuing the data on one of those. I've had issues with flash drives coming with weird pre-formatting that makes it look like junk in Linux. After you rescue the data, though, you should be able to format it as FAT32 and it will work on any modern platform.

---

