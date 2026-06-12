---
title: "Trying to dual boot"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by Ionamay on 2007-09-09
Okay so I want to dual boot XP and Ubuntu, and I have looked through some of the guides but when it comes to the partition bit, I'm a bit confused. In the guides I have read, it has a sliding bar thing to choose how much of the free space you want to use for Ubuntu, but I can't see that when I try and it says 'This probably happened because the selected disk or free space is too small to be automatically partitioned.' I'm too scared to do it manually :P I don't want to do something wrong. Please help me ^_^

---

### Post by por100pre1 on 2007-09-09
Before anything else login to Windows, use Disk Cleanup and remove all Restore Points exept the last one. Use Disk Defragmenter a couple of times and Backup all your Documents and Files to an external media or hard disk drive. Any partition shrinking can get messy so you better get prepared first! Come back when ready.

Hope this helps. :)

---

### Post by eapache on 2007-09-09
As por100pre1 said, clean up XP first, then choose custom and take a screenshot (the printscreen key on your keyboard). Post the image here using the attachments section under 'additional options', and I will provide a step-by-step guide specific for your setup.

---

### Post by cotcot on 2007-09-09
I prefer additionally to the above recommendations to use the gparted liveCD to create the necessary partitions and to shrink the windows partition. During install you can skip the partition making step and only indicate which existing partition you want for / , /home and swap.

---

