---
title: "second hard drive"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by allenyake on 2006-01-16
I have a second hard drive on my computer,but it doesn't show up.Windows always 
recognized it automatically,how do I make ubuntu recognize it as a slave?i am still very new to this any help would be appreciated.
allen

---

### Post by jasay on 2006-01-16
I'm assuming the second harddrive was formatted in windows and so has either the fat or ntfs filesystem.  Windows partitions can be mounted following the directions given [here]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions"). Unfortunately, NTFS support in linux is limited to read-only.

---

