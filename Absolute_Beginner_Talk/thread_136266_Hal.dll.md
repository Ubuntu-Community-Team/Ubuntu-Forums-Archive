---
title: "Hal.dll"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by TheCyrus on 2006-02-25
Well, my installation failed again. :cry:  Now, whenever i try to boot into windows, i get a "HAL.dll is missing or corrupt" message. So whenever i go to the recovery console, i get the prompt D:\Windows instead of C:\Windows. Can anyone help me get back to windows?

---

### Post by TheCyrus on 2006-02-25
also, how can i write to NTFS if Linux can't do that?

---

### Post by Terry of Astoria on 2006-02-28
I just got the same problem when I deleted the second partition on my first drive and then allowed Ubuntu's partitioner to automatically partition the free space. Silly Windows had installed itself on the D: drive, and I had overwritten it with Ubuntu.
  - There is a linux live cd that does write to NTFS, I think. I don't remember where I was reading about it . . .
I recommend trying some kind of boot disc CD and seeing what's on that drive.
Unfortunately my windows installation got trashed because I installed Ubuntu over it. I had thought that Windows was on C: but it was on D:. Oops. Silly Windows XP installed itself on D:! Now I'll have to learn to back up and then reinstall my bootloader. Think what I'll do, install Smart Boot Manager after I install grub to my Linux partition.

---

