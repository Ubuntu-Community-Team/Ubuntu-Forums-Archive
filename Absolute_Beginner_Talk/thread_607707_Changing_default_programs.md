---
title: "Changing default programs"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by mangurt on 2007-11-09
Greetings all,
I love using ktorrent, and would like to make that program my default bit torrent program.  I have no idea how to do this.  Any help would be greatly appreciate it.
Thanks

---

### Post by atomkarinca on 2007-11-09
right-click any torrent file, select properties, "open with" tab, select ktorrent and click close. that's about it.

---

### Post by mangurt on 2007-11-09
I tried doing that, and I end up getting like a window where I have to search through folders, and that's where I get lost at.

---

### Post by atomkarinca on 2007-11-09
then, when you are asked to browse for the file, under /usr/bin you can find ktorrent.

---

### Post by mcduck on 2007-11-09
> **mangurt said:**
> I tried doing that, and I end up getting like a window where I have to search through folders, and that's where I get lost at.

Pretty much every program puts it's executable file into /usr/bin/, so that's where you'll probably find it.

Other than that, the 'which'-command will give you path to the executable of a program. For example 'which firefox' will return '/usr/bin/firefox'

---

### Post by hyper_ch on 2007-11-09
you can just enter "ktorrent" there as it is located within an environement path.

---

