---
title: "Merge partitions?"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by Dekadence on 2006-09-21
Is there any posibillity that I merge partitions on same hard Drive without formatting ubuntu?
I have 1 NTFS partition with 22GB and one 15GB linux partition, and I would like to format NTFS, and merge 22GB partition with 15GB partition. Anyone knows if it is possible and if it is, what program should I use?

---

### Post by bernied on 2006-09-21
You want to run linux off an NTFS file-system - why?
This does not sound like a good idea, it is asking for a difficult life, and probably won't work anyway, unless NTFS file support in linux has suddenly got much better.

As far as I know, there is no way to merge partitions, this is especially unlikely when you have two different filesystems.

The best you might be able to do is to move everything on the smaller partition onto the larger, then delete the smaller partition and then resize the larger one. This would of course need you to have enough space on the larger partition to fit all the files from the smaller one.

Else, you could move all the files from the smaller partition onto some temporary storage - usb disk, multiple dvds etc, then delete, resize, move back.

But, again, this all sounds like a really bad idea to me.
What are you trying to achieve?

---

### Post by Dekadence on 2006-09-21
nah I've formatted now :) got pissed of... no no, you didn't understand: I wanted to have more space... I didn't need that NTFS, I could format it... nah forget it ;) no need anymore, thanks anyway

---

