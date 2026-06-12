---
title: "GParted Help - unallocated space..."
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by petersjm on 2006-07-16
Hi all, sorry if this has been asked before. I've done a search and come up with a few things, but nothing I can see that helps me out...

When I installed Ubuntu, it asked for a new partition size, so I gave it 30Gb of my 40Gb HDD. Turns out, though, that it allocated the 30Gb to the NTFS partition, leaving about 7Gb for ext3 (where all my Ubuntu files are, I believe?). So, I wanted to resize NTFS by taking 25Gb from it, which I've done. I now have 25Gb of unallocated space, but it won't let me add it to ext3. And I can't create a new partition because it says I can't have more than 4 (I have fat16, ntfs, ext3, extended/Linux-swap).

Does anyone have a clue how to use GParted to add the 25Gb unallocated space to ext3? Any help appreciated :)

EDIT: Okay, I've done a further search of the forums, and it seems if the unallocated space is *before* ext3 on the GParted list, I can't use it? I'll post a screenshot and let you see it... (unallocated on this shot is at 2Gb, not 25)

---

### Post by reacocard on 2006-07-16
It's true, you can't extend backwards. easiest thing to do is just reinstall. if you back up your /home directory, you'll be able to keep all your settings.

---

### Post by petersjm on 2006-07-16
Thanks, reacocard. I guess I'll just have to reinstall. But two questions: Will I have to reinstall WinXP too, on my other partition? And, "back up your /home directory" -- can I just copy it to CD and import it again later? Thanks.

---

### Post by reacocard on 2006-07-16
no you don't have to reinstall XP, and yes, you can just copy /home to a cd and copy it back later.

---

### Post by petersjm on 2006-07-17
Thanks, reacocard. I've done as you suggested. Thanks for your help.

---

