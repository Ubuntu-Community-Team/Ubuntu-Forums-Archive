---
title: "file system format?"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by amtnbiker16 on 2007-10-12
sorry if this has been covered already, but if it was, i couldnt find it

im installing 7.1 on my computer and i want to know which format would be best to put it in 
overall performance is what im going for, i want what is fastest and if possible, whatever will eat up less of my batery (if applcable)

---

### Post by Quillz on 2007-10-13
Go with the standard choice, ext3. It's stable, secure and fast, which is exactly what you're looking for.

---

### Post by ayenack on 2007-10-13
> **Quillz said:**
> Go with the standard choice, ext3. It's stable, secure and fast, which is exactly what you're looking for.

+1

There may be a slight speed increase if you use ext2 depending on what hardware you're using but you will not have a journaled file system so in the event of hard restarts you may have problems. Although it's far easier  to recover deleted files on ext2.

But if it was me unless I was running really old hardware I would go with ext3 as well.

Good luck.

---

### Post by bodhi.zazen on 2007-10-13
I have not noticed a significant difference in the day-to-day responsiveness of different file systems.

This is a good starting pint : [http://infohost.nmt.edu/~val/review/choosing.pdf](http://infohost.nmt.edu/~val/review/choosing.pdf)

Personally the most import and factor is stability, so I stay with ext3, which is not to say the others are less stable, it is just that I think ext3 has a slight edge in the event of a power failure.

---

