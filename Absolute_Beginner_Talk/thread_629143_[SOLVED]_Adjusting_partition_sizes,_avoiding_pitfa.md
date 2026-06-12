---
title: "[SOLVED] Adjusting partition sizes, avoiding pitfalls."
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by JillSwift on 2007-12-02
If I use (from a live CD) gparted to *increase* the size of an ext3 or ntfs partition, will I lose data in that partition?

Will I loose data in an ntfs partition if I *decrease* its size?

If I move a partition, will the data survive that?

[CENTER] (Yesh, no matter the answer backups will be made before I start =^_^= )

[LEFT]***[COLOR=DarkGreen]Fangu![/COLOR]***
[/LEFT]
[/CENTER]

---

### Post by thorwood on 2007-12-02
Ive had mixed results on that, sometimes Ive corrupted the NTFS partition and sometimes not.

---

### Post by Daveth on 2007-12-02
probably worth having a read through some of this stuff, for all things gparted.

[http://gparted-livecd.tuxfamily.org/documentation.php](http://gparted-livecd.tuxfamily.org/documentation.php)

---

### Post by Irony on 2007-12-02
I shrunk my 60 GB windows XP partition down to 10 GB without a problem.

You can copy linux partitions quite easily; [http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

---

### Post by njparton on 2007-12-02
To be safe I wouldn't adjust NTFS partitions with gparted, just stick to linux partitions.

Ajust windows partitions via windows to be on the safe side.

---

### Post by JillSwift on 2007-12-02
Thanks everyone! The best part of Ubuntu is its users. =^_^=

I'm off to start my partition tweaking. Wish me luck!

---

