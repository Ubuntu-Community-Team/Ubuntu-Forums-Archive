---
title: "Partition Error?"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Phoenix27 on 2007-10-16
When I select my Windows XP partition it gives me this error

"Error 13: Invalid or unsupported executable format."

How can I fix this?

---

### Post by Phoenix27 on 2007-10-16
Anyone?

---

### Post by roadrunner343 on 2007-10-16
What version of Ubuntu are you running? I don't think Ubuntu supported the NTFS partition fomat until 7.10 (I may be wrong, correct me if needed) and more than likely that is what your Windows XP partition is in. So if you are trying to open it in an older version of Ubuntu, that could be the problem.

---

### Post by Phoenix27 on 2007-10-16
> **roadrunner343 said:**
> What version of Ubuntu are you running? I don't think Ubuntu supported the NTFS partition fomat until 7.10 (I may be wrong, correct me if needed) and more than likely that is what your Windows XP partition is in. So if you are trying to open it in an older version of Ubuntu, that could be the problem.

It's NTFS and I'm using 7.10

---

### Post by MinstrelBoy on 2007-10-16
Download super grub and burn onto cd.    [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
I would then use testdisk to rescue your data from the windows partition and then run the recovery console from the windows cd and try bootfix or fixmbr, type help for list of commands.
You can then use super grub to restore your grub startup menu.

---

